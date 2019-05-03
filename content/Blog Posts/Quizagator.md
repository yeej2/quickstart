---
title: "Developing Quizagator "

featured_dev_image: "devimage.jpg"

---

## Overview

Quizagator is an online tool that allows the creation of tests to be made
through text based syntax as opposed to using a GUI. This means that a
quiz can be created through the use of a text editor. This allows the
creation of tests to be much simpler as there is no need to alter
the quizzes in the GUI tools. This system is created using Flask and
Python along with the use of a SQLite3 database which manages the quizzes
and results. A link to the project can be found
[here: Quizagator.](https://github.com/GatorEducator/quizagator)

## What I did.

I had created the base for this project. The base for the project created in Flask
was my Senior Thesis project. From this point, I started working in a team to
create a better system for teachers to create quizzes. To do this, I acted as
a team leader for the Flask development team. I instructed and overlooked, and led
the team in order to ensure a deployable product at the end of the working period.
I also worked to create test cases to increase code coverage. I was also in charge
of helping to review code so that it could be merged with minimal conflicts.
Here is a snippet of some code that I wrote.

```
def db_init():
    """Checks if database is already initialized, if not, create new one"""
    database_path = app.config["DATABASE"]
    if not os.path.exists(database_path):
        conn = sqlite3.connect(database_path)
        c = conn.cursor()

        # Create table - people
        c.execute(
            """CREATE TABLE people(
            person_id INTEGER PRIMARY KEY AUTOINCREMENT,
            isTeacher INTEGER,
            username TEXT,
            password TEXT,
            salt TEXT,
            name TEXT,
            email TEXT
            )"""
        )

        conn.commit()
        return conn
        return sqlite3.connect(database_path)
```

This code is shortened for simplicity purposes. It looks for a database and if
there is no database then it initializes a new one. This creates a table and schema
in the database.

I also helped to create this:

```
for question_id in answers:
    response = answers[question_id]
    db.insert_db(
        "INSERT INTO quiz_responses (student_id, quiz_id, question_id,"
        " response) VALUES (?, ?, ?, ?)",
        [flask.session["id"], quiz_id, question_id, response],
    )
```

This is found in the `students.py` file. This inserts the student's responses into
the database to be called later.

For more insight into the project. Please use the link above.

## My Experience

I had a lot of fun with this project. The team pulled through and we made the
deadline. There were many learning opportunities and we all pitched in as much
as we were able. I enjoyed acting as a leader for the team, and helping people
learn more as we went along. Helping others on top of doing my own work proved
to be difficult, however it was very rewarding and helped me to improve my own
understanding of Flask, Python, and HTML. I hope to work on another project
soon!
