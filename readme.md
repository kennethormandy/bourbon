[![Bourbon Sass Mixin Library](http://bourbon.io/images/shared/bourbon-logo.png)](http://bourbon.io)

***

## An old fashioned version of Bourbon, compatible with libsass

*This is a Node-sass port of the [Bourbon](http://bourbon.io) library. If you are looking for the original Ruby/Rails version, you can find it
[here](https://github.com/thoughtbot/bourbon).*

Bourbon is a library of pure sass mixins that are designed to be simple
and easy to use. No configuration required.

The mixins aim to be as vanilla as possible, meaning they should be as close to the original CSS syntax as possible.

The mixins contain vendor specific prefixes for all CSS3 properties for support
amongst modern browsers. The prefixes also ensure graceful degradation for older
browsers that support only CSS3 prefixed properties. Bourbon uses SCSS syntax.

## Requirements

- [Node](http://nodejs.org)
- [Node-sass](https://github.com/andrew/node-sass)

## Installation

To install as a development dependency, run:

```bash
npm install --save-dev old-fashioned
```

To use the command-line tool, when it’s ready:

```bash
npm install -g old-fashioned
```

## Usage

The `includePaths` property returns an array of paths for use in
node-sass' `includePaths` option.

```javascript
var bourbon = require('old-fashioned').includePaths;
```

You can then pass this array to your config options:

```javascript
var sass    = require('node-sass')
  , bourbon = require('old-fashioned').includePaths;

sass.render({
  file: './application.scss',
  success: function(css){
    console.log(css);
  },
  error: function(error) {
    console.log(error);
  },
  // If you have additional paths to include, do something like:
  // includePaths: bourbon.concat('other/path', 'another/path'),
  includePaths: bourbon,
  outputStyle: 'compressed'
});
```

Import Bourbon at the beginning of your main scss file:

```scss
@import "bourbon";
@import "other/scss/partial";
```

## Grunt Usage

### Using the grunt-sass task

The [grunt-sass](https://github.com/sindresorhus/grunt-sass) task uses
[node-sass](https://github.com/andrew/node-sass)
([libsass](https://github.com/hcatlin/libsass)) underneath, and is the recommended
way to use Grunt with node-bourbon.

Example config:

```javascript
grunt.initConfig({
  sass: {
    dist: {
      options: {
        includePaths: require('old-fashioned').includePaths
      },
      files: {
        'path/to/output.css': 'path/to/input.scss'
      }
    }
  }
});
```

### Using the grunt-contrib-sass task

If you are using the Ruby version of Sass, you will likely be better off using [Bourbon](https://github.com/thoughtbot/bourbon) over Old Fashioned. Alternatively, switch to grunt-sass and speed up your compile times.

# Testing

```
npm test
```

## Credits

This version of Bourbon is maintained by Kenneth Ormandy, heavily borrowing from Michael LaCroix’s [node-bourbon](https://github.com/lacroixdesign/node-bourbon). All credits for the original library goes to [thoughtbot, inc](http://thoughtbot.com/community):

> ![thoughtbot](http://thoughtbot.com/images/tm/logo.png)
>
> Bourbon is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/community)
>
> The names and logos for thoughtbot are trademarks of thoughtbot, inc.
>
> Got questions? Need help? Tweet at [@phillapier](http://twitter.com/phillapier).

License
-------

Old Fashioned is Copyright © 2014 Kenneth Ormandy. It is free software, and may be redistributed under the terms specified in the LICENSE file.
