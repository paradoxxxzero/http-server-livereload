# http-server-livereload
A monkey patch of http.server to call livereload when server_forever is called.

This is compatible with flask reload and tiny-lr (grunt watch).

## Usage

### Flask + grunt-contrib-watch

In your flask developpement run script:

```python
from my_app import app

try:
    from http_server_livereload import patch
    patch()
except ImportError:
    pass
    
app.run()
```

And in your Gruntfile:

```coffeescript
module.exports = (grunt) ->
  grunt.initConfig
    watch:
      options:
        livereload: true
```

Then run `grunt watch` and your changes will reload [livereload](http://livereload.com/#getting-started) enabled tabs.
