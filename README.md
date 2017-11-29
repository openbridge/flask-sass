flask-sass
==========

**This project is not maintained and abandoned. Feel free to fork.**

A small Flask extension that makes it easy to use Sass (SCSS) with your Flask application.

Why another one? Because [Flask-Scss](https://bitbucket.org/bcarlin/flask-scss) doesn't
compile ``@import``ed files, and I liked the simple way [flask-coffee2js](https://github.com/weapp/flask-coffee2js)
compiled CoffeeScript files.

Code unabashedly adapted from https://github.com/weapp/flask-coffee2js.


## Installation

### Install with PIP

    pip install git+https://github.com/imiric/flask-sass.git#egg=flask-sass


## Usage

You can activate it by calling the ``sass`` function with your Flask app as a parameter:

      from flaskext.sass import sass
      sass(app, input_dir='assets/scss', output_dir='static/css')

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
