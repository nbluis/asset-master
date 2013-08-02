asset-master
============

Sample using compass and uglifierjs outside of rails project.

### Usage

- Define *js* group files into *asset-master.yml*.
- Configure *compass* at *config.rb*.

### Rake tasks:

+ `rake watch`
Watch the javascript and scss files and compile when they changes.
+ `rake compile_js`
Manually compile all js files.
+ `rake compile_scss`
Manually compile all scss files.

### License
(The MIT License)