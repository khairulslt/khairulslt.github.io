---
title: An introduction to Django's ORM
date: 2019-04-24 15:27:31
---

At the start of 2019 I started working with [Django](https://www.djangoproject.com/){:target="_blank"}, a Python Web framework.

The nice thing about Django is that it comes with its own Object-Relational-Mapper (ORM) - meaning that you get to interact with your database in a nice Pythonical way instead of writing SQL queries. In short, its perfect for someone newer (like me) to learn the in's-and-out's of interacting with your database.

Let's look at a small example on creating an SQL Table called <strong>"Person"</strong> which will have two rows for its first and last name respectively.

1. <strong><u>Initializing an SQL database (without Django ORM)</u></strong>
    ```SQL
    CREATE TABLE myapp_person (
      "id" serial NOT NULL PRIMARY KEY,
      "first_name" varchar(30) NOT NULL,
      "last_name" varchar(30) NOT NULL
    );
    ```
Assuming a basic SQLite3 database, your code would probably look something like the above.
Seems lengthy? Yikes! Now, let's take a look at achieving something similar using the Django ORM instead.

2. <strong><u>Initializing an SQL database (with Django ORM)</u></strong>
    ```python
    from django.db import models

    class Person(models.Model):
        first_name = models.CharField(max_length=30)
        last_name = models.CharField(max_length=30)
    ```
Much, much cleaner. As for more technical specifics, a CharField is defined as a string field that we can use to define the rows in our database (should it accept a string/integer/boolean? etcetc.) You can configure it according to your needs. 
<br><br>Additionally, if you're wondering where the <strong> id </strong>field went, Django automatically adds it for you! Check out the docs on [different field types](https://docs.djangoproject.com/en/2.0/ref/models/fields/#field-types){:target="_blank"} & [automatic primary key fields](https://docs.djangoproject.com/en/2.2/topics/db/models/#automatic-primary-key-fields){:target="_blank"}

---

Now that we're happy with this database we've created, let's take a look at how we would access it with another SQL vs ORM example! The following code selects all the fields available in our <strong>Person</strong> table.

1. <strong><u>Database querying (without Django ORM)</u></strong>
    ```SQL
    SELECT * FROM myapp_person;
    ```
<br>
2. <strong><u>Database querying (with Django ORM)</u></strong>
    ```python
    all_entries = Person.objects.all()
    ```

---
Since we've gotten the non-exciting examples out of the way, let's take a look at some possible code we would actually use in jobs that we get paid for.

1. <strong><u>Get object by ID (without Django ORM)</u></strong>
    ```SQL
    SELECT * FROM Person WHERE id = {}.format(id)
    ```
<br>
2. <strong><u>Get object by ID (with Django ORM)</u></strong>
    ```python
    obj = Person.objects.get(id=this_object_id)
    ```
Bonus points if you spot the SQL injection error above :ghost:

I try and follow as much discussion as I can online about the disadvantages of using Django's ORM (unable to perform complex SQL queries, an ORM will never be an effective representation of the underlying data model, etcetc.)

But for the most part, either I'm fortunate (or some might argue, unfortunate) that I haven't come across any of the problems above in my daily work. So far, I haven't found anything that I haven't been able to achieve with this giant monolith.

If you're interested in my opinion, I subscribe to [Why Django Sucks, Except When It Doesn't](https://coffeeonthekeyboard.com/why-django-sucks-except-when-it-doesnt-664/){:target="_blank"}. 

<strong>TLDR: While you're arguing about what works and what doesn't, someone already shipped the next Facebook with PHP</strong>