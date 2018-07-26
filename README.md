### Summation

#### 1. Gemfile追加

```ruby
gem 'webpacker', github: "rails/webpacker"
```

#### 2. Bundle実行する

- Run

  `bundle install`

- Init webpack

  ```
    bundle
    bundle exec rails webpacker:install

    # OR (on rails version < 5.0)
    bundle exec rake webpacker:install
  ```

After the command lines above excuted, it rendered a ton of files likes :

```
  new file:   .babelrc
  new file:   .browserslistrc
  modified:   .gitignore
  new file:   .postcssrc.yml
  new file:   Gemfile.lock
  new file:   app/javascript/packs/application.js
  new file:   bin/webpack
  new file:   bin/webpack-dev-server
  modified:   config/environments/development.rb
  modified:   config/environments/production.rb
  new file:   config/webpack/development.js
  new file:   config/webpack/environment.js
  new file:   config/webpack/production.js
  new file:   config/webpack/test.js
  new file:   config/webpacker.yml
  modified:   package.json
  new file:   yarn.lock

```