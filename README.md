# flask-hello-world-ver2
<h2>Structure of directory</h2>
<pre>/hello-world
   ├── hello.py
   ├── app
   │    ├── __init__.py
   │    └── routes.py
   ├── .flaskenv
   ├── Procfile
   ├── requirements.txt
   └── .gitignore</pre>
<h2>Preparation</h2>
<ol>
 	<li>Make directory
<pre>mkdir hello-world
cd hello-world</pre>
</li>
 	<li>Create virtual environment for Heroku and Flask using Conda
<pre>conda create -n &lt;environment name&gt;
conda env list
activate &lt;environment name&gt;</pre>
</li>
 	<li>Install packages
<pre>conda install flask
pip install gunicorn</pre>
</li>
</ol>
<h2>Create "Hello World" Flask app</h2>
<ol>
 	<li>Create a __init__.py file in app folder
<pre>from flask import Flask

app = Flask(__name__)

from app import routes</pre>
</li>
 	<li>Create a rountes.py file in app folder
<pre>from app import app

@app.route('/')
@app.route('/index')
def index():
    return "Hello World!"</pre>
</li>
 	<li>Create a hello.py file in root folder
<pre>from app import app</pre>
</li>
</ol>
<h2>Run the app locally</h2>
<ol>
 	<li>Set FLASK_APP environment variable
<ol>
 	<li>If using command line;
<pre>export FLASK_APP=hello.py
set FLASK_APP=hello.py # for windows</pre>
</li>
 	<li>If using .flaskenv file;
<ol>
 	<li>install python-dotenv
<pre>pip install python-dotenv</pre>
</li>
 	<li>make .flaskenv file
<pre>FLASK_APP=hello.py</pre>
</li>
</ol>
</li>
</ol>
</li>
 	<li>Run local server
<pre>flask run</pre>
visit <a href="http://localhost:5000/">http://localhost:5000/</a></li>
</ol>
<h2>Deploy the app to Heroku</h2>
<ol>
 	<li>Create a requirements.txt file
<pre>pip freeze &gt; requirements.txt</pre>
</li>
 	<li>Create a Procfile
<pre>web: gunicorn hello:app --log-file -</pre>
</li>
 	<li>Create a .gitignore file
<pre>/.flaskenv
/app/__pycache__/</pre>
</li>
 	<li>Commit the app to git
<pre>git init
git add .
git commit -m "initial commit"</pre>
</li>
 	<li>Deploy the app to Heroku
<pre>heroku login
heroku create &lt;app name&gt;
git push heroku master
heroku open</pre>
</li>
</ol>
<h2>Deploy the app to Github</h2>
<pre>git remote add origin https://github.com/&lt;User ID&gt;/&lt;repository name&gt;
git push -u origin master</pre>
<h2>References</h2>
<ol>
 	<li><a href="http://clouddatafacts.com/heroku/heroku-flask/heroku_flask_getting_started.html" target="_blank" rel="noopener">Building your first Heroku App with Flask</a></li>
 	<li><a href="https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world">The Flask Mega-Tutorial Part I: Hello, World!</a></li>
</ol>
