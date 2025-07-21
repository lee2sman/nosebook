# Install
# 
## Reinstalling ruby/gems/bundler when this thing breaks every 6 months

*updated July 2025*

1. Remove old Gemfile and Gemfile.lock
2. Change Gemfile to look like this 2 line file:
```
source "https://rubygems.org"
gem 'github-pages'
```
3. Run `bundle install` (i added sudo even though it warns not to)
4. Then you can do the normal `bundle exec jekyll serve --baseurl ''`
