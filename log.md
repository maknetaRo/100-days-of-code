# 100 Days Of Code - Log

### Day 1: April 24, 2019
#(delete me or comment me out)

**Plans for Today**:
Work on a Django downloader app
1. Read the existing code
2. Create a Django app (module) in which admin can upload different kind of files and users can download the files.
* Start an app, add it to settings.
* Make a model Uploader.
* Make a list view.
* Create a template list view.
* Add an url.

**Today's Progress**:
I managed to start an Uploader app in Django. It's a part of a bigger project. I created a Document Model and registered it in admin.py and now I can upload documents as an admin. I also created a template (HTML page) where a list of all uploaded documents is supposed to be display.

**Thoughts:**
I managed to do the simplest part of the project. The list of documents doesn't show any documents:-(
**Link to work:**

**Plans for tomorrow**:
Find out how to display description / title of the uploaded file as an active link for download.
1. Display the titles of the uploaded files.
2. Learn how a downloader works.

**Resources**:
https://simpleisbetterthancomplex.com/tutorial/2016/08/01/how-to-upload-files-with-django.html
https://www.youtube.com/watch?v=MjwWzBiAMck
https://www.youtube.com/watch?v=b43JIn-OGZU

### Day 2: April 25, 2019
**Plans for Today**:
1. Create local copy of 100DaysOfCode repository.
2. Read about working with files in Python.
3. Watch videos about uploading and downloading files in Django.

**Today's Progress**:
1. Local copy of 100DaysOfCode - done.
2. & 3. I read about working with files and start watching a few videos but they
very mostly about uploading files or creating files.
Unfortunately I have a problem with migrations. I had to remove part of the database
and migrations files. And now I need time to fix migrations.

**Thoughts:** I found it difficult to concentrate on the project due to my work
problems. I also need to spend more time learning Python to be able to build things
from scratch without looking for everything online.

**Link to work:**

**Plans for tomorrow**:
1. Read carefully git rep with manga_download
2. Fix the migrations
3. Write path to file (function)
4. Write view to download files.
5. Read 10 - 20 pages of a book about Python

**Resources**:
1. https://help.github.com/en/articles/fork-a-repo
2. Automate the boring stuff with Python & Python Crush Course
3. https://github.com/m-marian/manga_download/blob/master/mdownload/custom_functions.py
4. https://stackoverflow.com/questions/15246661/downloading-the-fileswhich-are-uploaded-from-media-folder-in-django-1-4-3

### Day 3: April 26, 2019

**Plans for Today**:
1. Read carefully git rep with manga_download
2. Fix the migrations
3. Write path to file (function)
4. Write view to download files.
5. Read 10 - 20 pages of a book about Python
6. Solve 3rd project Euler - watch video: https://www.youtube.com/watch?v=Y3n-PA3QoAE&t=58s

**Today's Progress**:
1. Solved 2 Euler problems - finding the largest prime factor and finding
the largest product of 2 3-digits numbers that is a palindrome. (spent 3.5h)
2. Yuppie! Managed to fix migrations.
Articles that helped me to do it:
* [https://simpleisbetterthancomplex.com/tutorial/2016/07/26/how-to-reset-migrations.html] How to reset migrations
* [https://medium.com/@taranjeet/django-migrations-a-primer-35b0f7b87062] Django Migrations: A Primer
Those two shows how to check, show or reset migrations properly.
* [https://stackoverflow.com/questions/39254849/django-table-not-created-when-running-migrations-that-explicitly-create-table] Django table not created when running migrations that explicitly create table. (stackoverflow)
I didn't know about django_migrations table in database. I removed my model migrations in this
table and than did makemigration my_app and migrate my_app and now it's working correctly.

**Thoughts:**
Writing down plans and achievement really helps (at least so far).
I'm very happy I managed to fix the migration and I'm also glad that I solved two Euler problems. My code is not the most efficient but I've also learnt new ways. I hope working everyday on those problems will help to move my brain cells and teach me more mathematical thinking. I was pretty good at Math at school but it was years ago.
Feel to tried to work more on points 1, 3 and 4.

**Link to work:**

**Plans for tomorrow**:
1. Solve 5th Project Euler problem.
2. Write path to file (function)
3. Write view to download files.
4. Read 10 - 20 pages of a book about Python

**Resources**:
