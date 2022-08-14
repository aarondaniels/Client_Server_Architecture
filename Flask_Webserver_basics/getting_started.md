# What Is the Flask Web Server?

Flask is a web framework. This means Flask provides you with tools, libraries, and technologies that allow you to build a web application. Flask can also be used for building more complicated applications for release on the Web.

The entirety of the code written in Flask is in Python. This means that basic Flask applications need very few dependencies of their own. The downside of this is that if you want to create more complex applications, you will need to independently research some of the available plug-ins to achieve more complex results.

# What You Need to Start Building a Flask Application

Flask mainly relies on Python. For this reason, when you start using Flask to build a very simple website all you need is a working installation of Python, and of course, a text editor, such as VS Code.

Before you begin to create a Flask application, a wise preliminary step is to create a folder on your machine where you will store all the needed files for that application. You can do this by opening your Terminal window and creating a folder using the command mkdir <folder_name>.

Next, you will need to create a file, app.py, that will contain the code to build your application. Generally, this file has the following basic structure:

``` python
from flask import Flask

app = Flask(__name__)

@app.route('/')

def index():

    return 'Hello world'

if __name__ == '__main__':

    app.run(debug=True, host='0.0.0.0', port = 5000)

```
Note that the structure of the `app.py` file is used for creating a simple website that displays the words “Hello World”.

As you have learned in the previous videos in this module, you can also add requests, such as `GET` and `POST`, to make your HTTP requests more specific.

In the example file structure, “Hello World” is written as a simple string. To make your application more visually appealing, you can use HTML to write your text and add more details to your application, such as navigation bars, menus, and/or colors.

In order to include HTML code in your application, you will need to create a new folder titled `templates`, and insert a file called `index.html` in it. In this file, you will be able to include everything you want to be displayed as HTML in your application.

In order to render the HTML, you will also need to include the code `render_template` in the first line of the file `app.py`.

As a last step, you will need to define a Python decorator to read the `index.html` file. The simplest syntax to achieve this is as follows:

``` python
@app.route('/')

def index():

    return render_template('index.html')
```

The code above makes Flask look for `index.html` in the templates directory in which the app.py program is in.

You can add as many files as you need in the template folder, based on what you want your application to include. The important thing to remember while doing this is to add the necessary decorators to the `app.py` file in order to render those templates.

In conclusion, Flask is a powerful web framework that allows you to build websites using a simple interface and simple Python code.