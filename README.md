# flask-chairy
Flask-Chairy is a wrapper for PeeWee database

![Flask-Chairy](http://hellogiggles.com/wp-content/uploads/2015/02/24/Best-TV-Chairs-Peewee-Playhouse-Chairy.jpg)


Here is a snippet to setup a db connection. Will add docs and samples for MySQL and others
```python
from flask import Flask
from peewee import *

from flask_chairy.db import Database

DATABASE = {
    'name': 'example.db',
    'engine': 'peewee.SqliteDatabase',
}

app = Flask(__name__)
app.config.from_object(__name__) # load database configuration from this module

# instantiate the db wrapper
db = Database(app)

# start creating models
class Blog(db.Model):
    name = CharField()
    # .. etc
```


Other examples

To connect to MySQL using authentication:
```
DATABASE = {
    'name': 'my_database',
    'engine': 'peewee.MySQLDatabase',
    'user': 'db_user',
    'passwd': 'secret password',
}
```
If using a multi-threaded WSGI server:
```
DATABASE = {
    'name': 'foo.db',
    'engine': 'peewee.SqliteDatabase',
    'threadlocals': True,
}
```

