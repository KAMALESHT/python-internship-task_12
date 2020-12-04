# python-internship-task_12

1.Create a JSON of all object types and import the JSON into a SQL Database.

Solution:

task_12.py


x={"Name":"KAMALESH"

   ,"nickname":None,

    "age":20,

   "Languages known":["tamil","english","hindi","telugu","french"],

   "marks":{"math":90,"science":95,"english":94},

   "percentage":92,

   "single":True,

   "hobbies":("reading books","playing games","listening to music")

    }
   
sql.py


import json

import task_12

import sqlite3

conn = sqlite3.connect('task_12.db')

print("Database found");

c=conn.cursor()

c.execute('''CREATE TABLE BIO_DATA(data json);''')

print("Table:");

c.execute('''INSERT INTO BIO_DATA VALUES(?)''',(json.dumps(task_12.x),))

c.execute('''SELECT * FROM BIO_DATA''')

print(c.fetchall())

conn.commit()

c.close()

    

