# 100 Days Of Code - Log Round 4

### Day 6: April 29, 2019

**Plans for Today:**
1. Work on WhiteNoise configuration
2. Deploy
3. Write first blog post
4. Move back to building downloader
* writing path to files
* writing view to download file

**Today's Progress:**
Tasks 1 and 2 completed!!!
I need to learn testing my Django apps, it will save a lot of time during deployment.
But without tests and with server error (500), change DEBUG to True for a while to check what causes the problem. My problem was missing static/favicon.png file. I had the info locally but didn't pay the attention to it as the app worked on local server. After fixing errors turn DEBUG to False again.

**Thoughts:**
I'm pretty excited I managed to deploy the app on Heroku.

**Link to work:**
https://makneta.herokuapp.com/post/1/

**Plans for tomorrow:**
1. Get through this tutorial: https://realpython.com/working-with-files-in-python/

**Resources:**
1. Found and stored for later use: https://composingprograms.com/
2. Interesting but I don't know if helpful: https://medium.com/@flouss/streaming-a-file-through-django-a6dcff21e046
3. Another course to try: https://codefellows.github.io/sea-python-401d4/index.html#course-objectives


### Day 5: April 28, 2019

**Plans for Today:**

1. Manage docker to use django blog app locally
2. Check blog app and fix small issues
3. Deploy my blog
* how to hide secret keys
* how to use postgres database

**Today's Progress:**

Spent almost 4 hours coding - even more looking for solution.
1. I managed docker to run postgres  and then fixed small issues in the blog app itself.
2. But deployment is a nightmare.
I used python-decouple module to create .env file with secrets - secret_key, postgres user and password and so.
Important:
To add all dependences from requirements.txt to pipenv shell use:
$ pipenv install -r requirements.txt

I have done a lot to setup everything to deployment. First I wanted to deploy it to PythonAnywhere but it costs too much to have an app with postgres there. When I changed everything for Heroku, now I have problem with wsgi and such an error:
"File "/home/magda/.local/share/virtualenvs/myblog-F1Ww9ekw/lib/python3.7/site-packages/django/core/servers/basehttp.py", line 50, in get_internal_wsgi_application
    ) from err
django.core.exceptions.ImproperlyConfigured: WSGI application 'mysite.wsgi.application' could not be loaded; Error importing module."

And my app has been deployed on Heroku but there is an application error
"our WhiteNoise configuration is incompatible with WhiteNoise v4.0"

**Thoughts:**
A bit dissapointed that I haven't managed to deploy this app today.
No time for Python and project Euler.

**Link to work:**

**Plans for tomorrow:**
1. Work on WhiteNoise configuration
2. Deploy
3. Move back to building downloader.
* writing path to files
* writing view to download file

**Resources:**
1. https://www.pythonsetup.com/what-should-i-check-deploying-my-django-application-production/
2. https://github.com/kennethreitz/dj-database-url?fbclid=IwAR1n0U6lDd9aP3hYnGvIcJ7kdZ4NQuy9AllTGjV_SeqhnokwuTsGRLrHVQI
3. https://djangobook.com/deploying-django/
4. https://simpleisbetterthancomplex.com/series/2017/10/16/a-complete-beginners-guide-to-django-part-7.html
5. https://medium.com/@nithinkvijayan/https-medium-com-nithinkvijayan-separating-django-application-config-and-secrets-from-code-python-decouple-e0787d2bcc2a
6. https://simpleisbetterthancomplex.com/2015/11/26/package-of-the-week-python-decouple.html
7. https://dev.to/achiengcindy/laughing-blog-tutorial-part-1-project-structure-21fi
8. https://realpython.com/pipenv-guide/


### Day 4: April 27, 2019

**Plans for Today:**
1. Find out how to prepare Django app to deployment on PythonAnywhere
* how to hide secret keys
* how to use postgres database on PA
2. Deploy my blog
3. Write the first article
4. Solve 5th Project Euler Problem

**Today's Progress:**
1. Managed to solve the 5th Project Euler problem. I did it "on foot" and now have to analyze the solution from internet because I can't grasp it fully.  

**Thoughts:**
Project Euler mathematical problems are really tiring.
I usually plan a lot on Saturday or Sunday but then I have not enough time to do it. And today I only managed to do project Euler and read a few articles on PythonAnywhere about deploying Django app.
Need to learn how to solve problem when I have a few app that use Postgresql or MySQL as I am not able to run my blog locally due to server already in use problem.

**Link to work:**

**Plans for tomorrow:**
1. Find out how to prepare Django app to deployment on PythonAnywhere
* how to hide secret keys
* how to use postgres database on PA
2. Deploy my blog
3. Write the first article

**Resources:**

1. https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment
2. https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/
3. https://help.pythonanywhere.com/pages/environment-variables-for-web-apps/
4. https://help.pythonanywhere.com/pages/DeployExistingDjangoProject/
5. https://www.laurenwood.org/anyway/2016/04/setting-up-on-pythonanywhere/
6. https://www.pythoncircle.com/post/18/how-to-host-django-app-on-pythonanywhere-for-free/


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
to use later on
* https://realpython.com/read-write-files-python/
* https://realpython.com/working-with-files-in-python/
* https://realpython.com/pdf-python/
* https://realpython.com/courses/python-requests/


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

<!-- ##Template
### Day 0: April 01, 2019

**Plans for Today:**

**Today's Progress:**

**Thoughts:**

**Link to work:**

**Plans for tomorrow:**

**Resources:** -->
