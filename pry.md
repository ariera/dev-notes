# Cool commands cheatsheet

* try-again
* edit -c
* cd-cause
* copy-history

# Gemfile

```ruby
group :test, :development do
  gem 'pry'
  gem 'pry-doc'
  gem 'pry-rails'
  gem 'pry-byebug'
  gem 'pry-rescue'
  gem 'pry-clipboard'
end
```

# ~/.pryrc

```ruby
# switch default editor for pry to sublime text
Pry.config.editor = "subl"

# format prompt to be <Rails version>@<ruby version>(<object>)>
Pry.config.prompt = proc do |obj, level, _|
  prompt = "\e[1;30m"
  prompt << "#{Rails.version} @ " if defined?(Rails)
  prompt << "#{RUBY_VERSION}"
  "#{prompt} (#{obj})>\e[0m"
end

Pry.commands.alias_command 'subl', 'edit -c'

if defined?(PryByebug)
  Pry.commands.alias_command 'c', 'continue'
  Pry.commands.alias_command 's', 'step'
  Pry.commands.alias_command 'n', 'next'
  Pry.commands.alias_command 'f', 'finish'
end

if defined?(PryClipboard)
  Pry.commands.alias_command 'cp', 'copy-history'
end
```
