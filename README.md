flask-sass
==========

A small Flask extension that makes it easy to use Sass (SCSS) with your Flask application.

This was forked as we use it in our projects and wanted to make sure a copy was available if the [original](https://github.com/imiric/flask-sass) was ever removed.


The original creator adapted from https://github.com/weapp/flask-coffee2js to perform the same task for sass


## Installation

### Install with PIP

    pip install git+https://github.com/openbridge/flask-sass.git#egg=flask-sass


## Usage

You can activate it by calling the ``sass`` function with your Flask app as a parameter:
Your output dir should be located in the static directory.

      from flaskext.sass import sass
      sass(app, input_dir='assets/scss', output_dir='css')

This will intercept the request for ``output_dir/*.css`` and compile the file if it is
necesary using the files from ``input_dir/*.scss``.

When you deploy your app you might not want to accept the overhead of checking
the modification time of your ``.scss`` and ``.css`` files on each request. A
simple way to avoid this is wrapping the sass call in an if statement:

      if app.debug:
          from flaskext.sass import sass
          sass(app)
          
If you do this you'll be responsible for rendering the ``.scss`` files into
``.css`` when you deploy in non-debug mode to your production server.
