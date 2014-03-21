---
title: '安裝 Redmine  1.1.1 遇到 version_requirements 的暫時解法'
author: TaopaiC
layout: post
permalink: /2011/03/08/329
categories:
  - Ruby
---
裝 redmine 1.1.1 會遇到

<pre class="brush: plain; title: ; notranslate" title="">undefined local variable or method `version_requirements' for #&lt;Rails::GemDependency:0x9031db8&gt;
</pre>

幾種解法:

1.  將 gem 換回 1.4.2 <pre class="brush: bash; title: ; notranslate" title="">$ gem install rubygems-update -v='1.4.2'
$ gem uninstall rubygems-update -v='1.5.0'
$ update_rubygems
</pre>

2.  使用更新的 redmine , 例如 trunk 版本
3.  在 config/environment.rb 中, engines 之後, Initializer 之前加入 <pre class="brush: ruby; title: ; notranslate" title="">begin
  require File.join(File.dirname(__FILE__), '../vendor/plugins/engines/boot')
rescue LoadError
# Not available
end

# 加入這段
if Gem::VERSION &gt;= "1.3.6" 
    module Rails
        class GemDependency
            def requirement
                r = super
                (r == Gem::Requirement.default) ? nil : r
            end
        end
    end
end

Rails::Initializer.run do |config|
</pre>

4.  在 rails 2.3 引入 Bundler , [教學][1]

我個人兩個站各是用 2,3 的方法.

參考資料:

*   [#7516 Redmine does not work with RubyGems 1.5.0][2] 
*   [undefined local variable or method \`version_requirements’ for # (NameError) | Chris Oliver][3]

 [1]: http://gembundler.com/rails23.html
 [2]: http://www.redmine.org/issues/7516#note-3
 [3]: http://excid3.com/blog/2011/02/undefined-local-variable-or-method-version_requirements-for-nameerror/