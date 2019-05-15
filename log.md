# 100 Days Of Code - Log Round 4

### Day 17: May 15, 2019

**Plans for Today:**
1. Start creating Event module in Django edu_app - first plan and write a bit of pseudo-code on paper.
2. Python Tutorial chapter 5 Data Structures
3. C++ course
4. DataWorkshop day 2 and 3

**Today's Progress:**

**Thoughts:**

**Link to work:**

**Plans for tomorrow:**

**Resources:**

### Day 16: May 14, 2019

**Plans for Today:**
1. Start creating Event module in Django edu_app
2. Python Tutorial chapter 5 Data Structures
3. C++ course
4. DataWorkshop day 2

**Today's Progress:**
1. Started only watching DataWorkshop video and doing the task when my computer froze for several minutes and then shut down all the programs I was using.
2. Did lesson 2 of C++ course  

**Thoughts:**
* Unfortunately I'm not interested in self driving cars.
* Didn't have much time for coding as I wrongly planned my free time. I simply forgot that I promised my daughter to watch Eurovision with her.


**Link to work:**

**Plans for tomorrow:**
1. Start creating Event module in Django edu_app
2. Python Tutorial chapter 5 Data Structures
3. C++ course
4. DataWorkshop day 2 and 3

**Resources:**
* https://dev.to/aspittel/moving-past-tutorials-8-tips-for-problem-solving-3e0p

### Day 15: May 13, 2019

**Plans for Today:**
1. DataWorkShop challenge day 1
2. Read about lambda functions on Python Official Tutorial
3. Read about reusable apps in Django

**Today's Progress:**
1. DataWorkshop challenge Day1
* Installed pyenv to be able to use anaconda, although I'm not sure if it wouldn't be enough only uncomment some code in ./bashrc

* installed new libraries socketio, flask and evenlet and then package udacity/self-driving-car-sim https://github.com/udacity/self-driving-car-sim and played for a while.

![](images/Screenshot_from_2019-05-13.png)

2. Finished chapter 4 of The Python Tutorial and additional article about lambda.
Not much code written, only a few examples.

3. Decided not to do reusable app in Django (at least for now)

**Thoughts:**
* I'm curious what we will be doing through the next days of the challenge. I'm not particularly interested in ML but it's good to broaden horizons and I have an ability to learn at least a bit about different Python libraries.
* I've known about lambda but haven't used it on my own. Really don't know where to use except coding exercises.

**Link to work:**

**Plans for tomorrow:**
1. Start creating a new app Django app with events and location. Need to create a table in a template to add there town, voivodeship, postal zip and geographic coordinates. Should I use GeoDjango?  
2. Python Tutorial chapter 5 Data Structures

**Resources:**
1. https://books.agiliq.com/projects/django-orm-cookbook/en/latest/table_name.html?fbclid=IwAR2ZbHX70u6zk1A-oeys1ljQoHVgvrFoxTxmas0m9zIpYTwnLeCyklRA9wI
2. https://realpython.com/courses/make-location-based-web-app-django-and-geodjango/
3. https://realpython.com/location-based-app-with-geodjango-tutorial/

### Day 14: May 12, 2019

**Plans for Today:**
1. Work on downloader app - showing all categories with links in each
2. Review functions in Python: esp. lambda and using  args and kwargs

**Today's Progress:**
1. Learnt to remove a git commit if it hasn't been pushed to remote:
`git reset HEAD~1`
than check if working copy is clean by `git status``
* If the changes have been pushed to remote, the `git revert HEAD` should work.
2. Learnt also how to remove file from repository
```
git rm --cached `git ls-files -i -X .gitignore`
```
3. All categories with links in one template - DONE
* In filecategory_list.html I used category.document_set.all to do it.
My code in filecategory_list.html
```
{% extends "two_column.html" %}
{% load staticfiles %}

{% block main %}

<h2 id="title">Lista dokumentów do pobrania</h1>
  {% for category in object_list %}
<h3> {{ category }}</h3>  

  <ul>
    {% for document in category.document_set.all %}

  <h3><a href="{{ document.document_url }}">
    {{ document.description }}</a></h3>

    {% empty %}
      None
    {% endfor %}
  </ul>

  {% endfor %}
{% endblock %}
```

* Worked also on auto generating slug. I've got two models in this app - Document and FileCategory and I added slug to FileCategory model. I needed to import slugify from django.utils.text and then create a get_unique_slug function and a save function.

* I wanted also to have a default category called 'INNE' (others) so I added this feature in title
Part of my models.py code:
```
from django.db import models
from django.utils.text import slugify

class FileCategory(models.Model):
    title = models.CharField(max_length=250, default='INNE')
    slug = models.SlugField(max_length=250, unique=True, blank=True)

    class Meta:
        verbose_name = 'Kategoria Plików'
        verbose_name_plural = 'Kategorie Plików'
        ordering = ('title',)

    def __str__(self):
        return self.title

    def _get_unique_slug(self):
        slug = slugify(self.title)
        unique_slug = slug
        num = 1
        while FileCategory.objects.filter(slug=unique_slug).exists():
            unique_slug = '{}-{}'.format(slug, num)
            num += 1
        return unique_slug

    def save(self, *args, **kwargs):
        if not self.slug:
            self.slug = self._get_unique_slug()
        super(FileCategory, self).save(*args, **kwargs)
```
4. I'm going through Python Official tutorial because I can see I forget a lot of Python. Today was reading about defining functions and using default, keyword arguments as well as args and kwargs

**Thoughts:**
It was such a long day.
* I finished one Django module, manage to push it on bitbucket and then made a pull requests.
* Talked to my colleague about the next module in our Django app - events with location and the other one Categories which should be a reusable app (at least I think so)
* I really wish I had more time to do everything that seems interesting.  

**Link to work:**

**Plans for tomorrow:**
1. Read about lambda functions on Python Official Tutorial
2. Read about reusable apps in Django
3. I almost forget that tomorrow starts the 3rd part of Machine Learning Challenge, so make the first day tasks.

**Resources:**
* https://fazle.me/auto-generating-unique-slug-in-django/
* For tomorrow:
* https://www.afternerd.com/blog/python-lambdas/
* https://django-reusable-app-docs.readthedocs.io/en/latest/
* https://anthony-monthe.me/weblog/2018/01/02/50-tips-maintain-django-reusable-app/
* https://stackoverflow.com/questions/21811851/how-do-you-actually-use-a-reusable-django-app-in-a-project

### Day 13: May 11, 2019

**Plans for Today:**
1. Continue C++ course
2. Work on downloader app - showing all categories with links in each
3. Review functions in Python: esp. lambda and using  args and kwargs
4. Continue HTTP & Web Servers Course

**Today's Progress:**
1. Finished first lesson of C++ course - 14 to go.
2. Spent sometime taking notes while reading Lesson 1 of HTTP & Web Servers Udacity course. Learnt about URIs, hostnames and ports.

**Thoughts:**
* I'm a bit surprised that I really like both Udacity courses. They are interesting, the videos are rather short and the texts and exercises are easy to understand.

* The HTTP & Web Servers Course helps me to neaten my knowledge.

**Link to work:**
1. C++ exercises:
* https://github.com/maknetaRo/learn_cplusplus/blob/master/yardage.cpp
* https://github.com/maknetaRo/learn_cplusplus/blob/master/workCin.cpp
* https://github.com/maknetaRo/learn_cplusplus/blob/master/withMain.cpp
* https://github.com/maknetaRo/learn_cplusplus/blob/master/roomArea.cpp
* https://github.com/maknetaRo/learn_cplusplus/blob/master/name.cpp
* https://github.com/maknetaRo/learn_cplusplus/blob/master/factfile.cpp

**Plans for tomorrow:**
1. Work on downloader app - showing all categories with links in each
2. Review functions in Python: esp. lambda and using  args and kwargs

**Resources:**
* https://classroom.udacity.com/courses/ud210
* https://classroom.udacity.com/courses/ud303

### Day 12: May 10, 2019

**Plans for Today:**
1. 1 hour of C++
2. Review functions in Python
3. HTTP and Web Servers 1 hour

**Today's Progress:**
1. Managed to start C++ course on Udacity. I'm in the middle of the first lesson.
2. Did two tasks from Rosetta Code website
3. Started HTTP and Web Servers course

**Thoughts:**
Unfortunately my family problems have been a big issue for last days and I can't concentrate fully on learning. I feel tired and irritated almost all the time.
I'm glad I managed to overcome my fear connected wit using Git and managed to merge a conflicting file and added a repository from my new computer to a Github repo created a few months ago.
I really like doing Python exercises.

**Link to work:**
* https://github.com/maknetaRo/learn_cplusplus
* https://github.com/maknetaRo/mega_list/blob/master/beer_song.py
* https://github.com/maknetaRo/mega_list/blob/master/christmas_song.py

**Plans for tomorrow:**
1. Continue C++ course
2. Work on downloader app - showing all categories with links in each
3. Review functions in Python: esp. lambda and using  args and kwargs
4. Continue HTTP & Web Servers Course

**Resources:**
* https://classroom.udacity.com/courses/ud210/lessons/1343a461-102f-41e1-b505-bf9ec62f427b/concepts/60086a00-e0b3-417f-8f73-77fd16314b9e
* https://classroom.udacity.com/courses/ud303


### Day 11: May 08, 2019

**Plans for Today:**
1. Python Official Tutorial (I need some Python revision)

**Today's Progress:**
1. Almost no progress, only I reminded myself a Fibonacci algorithm

**Thoughts:**
Haven't been coding recently mostly because of my addiction to crime stories but today I couldn't been able to concentrate because of my son's meltdown.

**Link to work:**

**Plans for tomorrow:**

**Resources:**
<!-- * https://stackabuse.com/introduction-to-pythons-collections-module/
* https://www.youtube.com/watch?v=8DvywoWv6fI&t=80s -->
* https://docs.python.org/3/tutorial/controlflow.html

### Day 10: May 05, 2019

**Plans for Today:**
1. Write a blog post
2. Working on categories in file downloader app
3. Start a new Python task from Project Euler or Mega List.

**Today's Progress:**
1. I managed to write a blog post about starting a Django project.
2. Started a new Python project: binary to decimal. So far managed only to check if the user is giving no more than 8 digits and if all the digits are 0 or 1.

**Thoughts:**
I like writing about Django even though it's very tiring. And to write regularly I need to create these blog posts in chunks.
I still can't remember how to convert binary numbers into decimal ones. Creating the converter needs a lot of reading.

**Link to work:**
1. Link to blog post: https://makneta.herokuapp.com/post/3/
 * and to source code on Github: https://github.com/maknetaRo/website/tree/master

**Plans for tomorrow:**
1. Read about binary and decimal numbers.
2. Write a binary to decimal converter.
3. Work on displaying categories in Django file downloader.

**Resources:**
1. This blog post and all the links that are at the end of it.
 https://medium.com/basecs/bits-bytes-building-with-binary-13cb4289aafa

### Day 9: May 04, 2019

**Plans for Today:**
1. Finish Change Return Program
2. Start a new Python program.
3. Link the download app to the main page.
4. Add categories and slugs to the list of files in Django.
5. Read about slug and publish_date in Django app and change model in blog app.

**Today's Progress:**
#### 1. Finished Change Return Program.
I had to look a bit for a solution. Using if-clauses generated many lines of code and a lot of repetition. I didn't like that solution so I checked and found out a shorter and much better solution.
In this solution the number is first divided by the biggest number -the biggest note value (or coin) and then the modulo is divided by the next number. And so on, until nothing is left.

If the change (in my code it's called zlotych) equals 78\
`fifty_zloty = zlotych // 50`\
this division equal 1 - it means it is 1 50zl note.\
and now the modulo of 78 and 50\
`zlotych %= 50`\
equals 28\
Now 28 is divided by 20\
`twenty_zloty = zlotych // 20`\
and it equals 1 - it means it is 1 20zl note\
After the next operation\
`zlotych %= 20`\
we've got 8zl left\
8 zloty divided by 10 equals 0 - so there are 0 10zl notes.\
`ten_zloty = zlotych // 10`\
`zlotych %= 10`\
so we still have 8 zloty left and this 8 zloty is used in the next operation\
`five_zloty = zlotych // 5`\
`zlotych %= 5`\
it gives 1 5zl coin and there is still 3 zloty left\
In the next step we divide 3 by 2\
`two_zloty = zlotych // 2`\
and we have 1 2zl coin and 1 zloty left.\
`zlotych %= 2`\
And it means there is also 1 coin 1zl\
`one_zloty = zlotych // 1`\

2. I did the next coding task from mega_list, credit card validation, using Luhn algorithm.
In this algorithm firstly, we have to drop the last digit and then reverse the number. The next step is to double every second digit and if the value of the multiplied digit is bigger than 9 we have to subtract nine from the number. Than we have to sum all the digits together and if the modulo 10 of this sum equals the value of the digit we dropped at the beginning, the credit card is valid.

3. Module linked to the main page navigation

4. Added new model FileCategory with title and unique slug. Now need to work on displaying files by categories in the main document list view. I'd like to choose one default category but don't know it is possible.

**Thoughts:**
Pretty like mathematical exercises. I was a bit avoiding working on Django.
I've been planning to write at least one post on my blog a week but now I feel hesitant as I'm afraid I have nothing important to write and my Django knowledge is not enough to write about creating an app.

**Link to work:**
1. https://github.com/maknetaRo/mega_list/blob/master/numbers2.py
2. https://github.com/maknetaRo/mega_list/blob/master/card_validation.py

**Plans for tomorrow:**
1. Working on categories in file downloader app
2. Write a blog post
3. Start a new Python task from Project Euler or Mega List.  

**Resources:**
Creating categories in Django
1. https://www.google.com/search?client=ubuntu&channel=fs&q=categories+in+django&ie=utf-8&oe=utf-8
2. https://stackoverflow.com/questions/38024594/how-to-add-categories-at-my-django-blog


### Day 8: May 02, 2019

**Plans for Today:**
1. Resolve problem with using polish letters in a description and in document title.
2. Finish Change Return Program
3. Read about slug and publish_date in Django app and changing model in blog app.
4. Project Euler problem 7
5. Creating blog post about Django

**Today's Progress:**
1. So resolving the problem with polish letters was pretty easy - I had to change encoding from latin-swedish to utf8-polish-ci in database. I'm using phpmyadmin in this project so it was an easy task.
2. I have had a few ideas how to solve this tasks. But my code is very long and I haven't finished it yet. I'm using only if statements. And they are a bit complicated.

**Thoughts:**
I have a feeling that there must be a better way to write this change return program. Perhaps I should have used classes or at least functions.

**Link to work:**

**Plans for tomorrow:**
1. Add categories and slugs to the list of files in Django.
2. Link the download app to the main page.
3. Finish Change Return Program
4. Read about slug and publish_date in Django app and changing model in blog app.
5. Creating blog post about Django

**Resources:**

### Day 7bis: May 01, 2019

**Plans for Today:**
1. Work on file downloader
2. Project Euler problem 6

**Today's Progress:**
1. Managed to display active links, but only if they don't have polish letters in the description.
2. 6th problem of PE was very easy.
3. Started solving Python tasks from Mega Project List. Did one (printing pi to nth digit) and started another - change return program where I have to figure out the change (done) and the number of quarters, dimes and so.  I'm going to use Polish currency.

**Thoughts:**
I spent so many hours and it occurred that I needed only small amount of code and I was overcomplicating everything as usually.

**Link to work:**
https://github.com/maknetaRo/mega_list

**Plans for tomorrow:**
1. Creating blog post about Django
2. Project Euler problem 7
3. Read about slug and publish_date in Django app and changing model in blog app.
4. Finish Change Return Program

**Resources:**
https://github.com/maknetaRo/Projects

### Day 7: April 30, 2019

**Plans for Today:**
Get through this tutorial: https://realpython.com/working-with-files-in-python/

**Today's Progress:**
Read the tutorial.

**Thoughts:**
Too tired to do anything more than reading.

**Link to work:**

**Plans for tomorrow:**

**Resources:**


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
