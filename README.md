### Summation

#### 1. Gemfile追加

```ruby
gem 'webpacker', github: "rails/webpacker"
```

#### 2. Bundle実行する

- Run

  `bundle install`

- Init webpack

  ```ruby
    bundle
    bundle exec rails webpacker:install
    # OR (on rails version < 5.0)
    bundle exec rake webpacker:install
  ```

After those command lines above were executed, it rendered a ton of files likes :
(webpacker導入時に生成されたファイル)

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


#### 3. Webpacker設定
##### Yarn Integrity
By default, in development, webpacker runs a yarn integrity check to ensure that all local JavaScript packages are up-to-date.
```
# Default (既定)
#config/environment/development.rb
config.webpacker.check_yarn_integrity = true

# Turn off (消す)
#config/environment/production.rb
config.webpacker.check_yarn_integrity = false
```

##### JS追加

By the default, webpack use yarn as package manager for node modules.
So if you wanna add new js module, use:
```ruby
yarn add {module}
```

Example(例):
- jquery
```ruby
 yarn add jquery
```
- boostrap

```ruby
yarn add boostrap
```
...

Check `package.json`, your Js module is add on `dependencies`

```ruby
{
  "name": "webpack_project",
  "private": true,
  "dependencies": {
    "@rails/webpacker": "^3.5.5",
    "boostrap": "^2.0.0",
    "jquery": "^3.3.1"
  },
  "devDependencies": {
    "webpack-dev-server": "^3.1.5"
  }
}

```

#### 4. Usage-使用法
##### Struct

```
app/javascript:
  ├── packs:
  │   # only webpack entry files here
  │   └── application.js
  └── src:
  │   └── application.css
  └── images:
      └── logo.svg
```

##### Include
Change `/views/layouts/application.html.erb`

```ruby
    <%# stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%# javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>

    ->
      <%= javascript_pack_tag 'application' %>
      <%= stylesheet_pack_tag 'application' %>
```
For `image_path`

```ruby
  <%= asset_pack_path 'images/logo.svg' %>
```

Sometimes, only change `<%= javascript_pack_tag 'application' %>` for JS module. Do need to use for `css` or `image`.

