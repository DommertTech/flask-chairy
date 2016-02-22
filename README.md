# flask-chairy
Flask PeeWee Database extension 



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
