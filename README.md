

# Tweaking-Gulp-Error-In-Laravel 5.3
Error:  Gulp cannot find module laravel elixir in Laravel-5.3

Two days into laravel I'm already loving it.

If you have a problem with running gulp on your newly installed laravel 5.3,
 you can use this simple tweak.

# Steps:

**(1)** After installing npm using  windows command prompt 
(or any CLI) with `npm install` make sure you can easily run gulp, 
if you can then there will be no need for step (2).


**(2)** When running gulp (_i.e to ensure gulpfile,js is included in your Laravel 5.3 Project_) 
if you get this uncommon error 


`module.js:340
    throw err;
          ^
Error: Cannot find module '.\vendor\laravel\elixir\Elixir'
    at Function.Module._resolveFilename (module.js:338:15)
    at Function.Module._load (module.js:280:25)
    at Module.require (module.js:364:17)
    at require (module.js:380:17)
    at Object.<anonymous> (H:\Binary\nginx\foobar.com\Gulpfile.js:1:76)
    at Module._compile (module.js:456:26)
    at Object.Module._extensions..js (module.js:474:10)
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Module.require (module.js:364:17)`
follow step (3)

**(3)** Go to _Gulpfile.js_, change the first line from _
(a) `const elixir = require('laravel-elixir')` 
to (b) `var elixir = require('laravel-elixir');`,_ . 
as shown below 
 


(a)
`const elixir = require('laravel-elixir');`

`require('laravel-elixir-vue');`

`/*`
 `|--------------------------------------------------------------`
 `| Elixir Asset Management`
 `|--------------------------------------------------------------`
 `|`
 `| Elixir provides a clean, fluent API 
  for defining some basic Gulp tasks`
 `| for your Laravel application. 
  By default, we are compiling the Sass`
 `| file for our application, as well as
  publishing vendor resources.`
 `|`
 `*/`

`elixir(mix => {`
    `mix.sass('app.scss')`
       `.webpack('app.js');`
`});`



(b)

`var elixir = require('laravel-elixir');`

`require('laravel-elixir-vue');`

`/*`
 `|--------------------------------------------------------`
 `| Elixir Asset Management`
 `|--------------------------------------------------------`
 `|`
 `| Elixir provides a clean, fluent
  API for defining some basic Gulp tasks`
 `| for your Laravel application. 
  By default, we are compiling the Sass`
 `| file for our application, as well as
   publishing vendor resources.`
 `|`
 `*/`

`elixir(mix => {`
    `mix.sass('app.scss')`
       `.webpack('app.js');`
`});`



(3) Then updated _packages.json_ with `"laravel-elixir": "*",`, 
 (if you use Laravel 5.3 there might be no need to update this.)

`{`
  `"private": true,`
  `"scripts": {`
    `"prod": "gulp --production",`
    `"dev": "gulp watch"`
  `},`
  `"devDependencies": {`
    `"bootstrap-sass": "^3.3.7",`
    `"gulp": "^3.9.1",`
    `"jquery": "^3.1.0",`
    `"laravel-elixir": "^6.0.0-9",`
    `"laravel-elixir-vue": "^0.1.4",`
    `"laravel-elixir-webpack-official": "^1.0.2",`
    `"lodash": "^4.14.0",`
    `"vue": "^1.0.26",`
    `"vue-resource": "^0.9.3"`
  `}`
`}`

 

(4)  Run _npm install_ again. After that you should be able to easily run gulp
 without any problem. Cheer...

If you use a Windows CLI below is what you should get.

# Screenshot:

![](https://pbs.twimg.com/media/CuGYYoBWEAEZLfs.jpg)


# Supporting information

 For my production Server:
 
 I'm currently using a WampServer

- Version 3.0.4 64bit
- Apache 2.4.18 - PHP 5.6.19 
- MySQL 5.7.11
- PHP 5.6.19 for CLI (Command-Line Interface)




# Credits

Ose Daniel  

Laravel.io


# Was this helpful ?

If this is worth a Fork, Star please endeavor to do so. 


# Contributing 

Please feel free to contribute by submitting a pull request to add to this help in solving gulp Error in Laravel 5.3.


Follow on [Twitter](https://twitter.com/exxonose) to show some love.

Thanks! Ose Daniel






