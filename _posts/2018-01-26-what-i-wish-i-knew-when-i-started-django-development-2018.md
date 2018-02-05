---
excerpt: A few points I wish I knew when I started out with Django, that would save myself tons of time and effort.
header:
  overlay_image: /assets/images/chris-ried-how-to-start-a-django-project.jpg
  caption: "Photo by Chris Ried on [**Unsplash**](https://unsplash.com)"
  overlay_filter: 0.5
  show_overlay_excerpt: true
  excerpt: "Django - What to note when you start a new projects  - updated for 2018"
toc: true
toc_label: "Django development"
toc_icon: "cog"
---
A few points I wish I knew when I started out with Django, that would save myself tons of time and effort.

TLTR: use [cookiecutter-Django](https://github.com/pydanny/cookiecutter-django) so you have most of stuff ready to use.

---

I started out with web development as mediocre PHP developer, never bother looking too much at docs, always struggle and Google always comes to the rescure (well, still).

I hate it when things are mixed up, and it's too hard to read and understand other people's code, or even mine from a few weeks ago. And this is important, 'cause reading code makes up huge amount of time.

Then Python (and Django) comes to the rescure. It's much easier to read, for the first time, I can read other people's code with ease (not all haha). And by reading others' code, my skills actually improve quite a lot. However, still, like anyone, In started out with tons of mistakes, especially with Django.

This is just a list of things I want to keep and will be adding along on stuff that I wished I knew when I started.

## Cookie cutter Django
Each time when I start a new project, I'll start off with a blank project with nothing, that I need to change it to whatever setting/structures I want, over and over again.

I thought I would create a repo for new project so I can start it from there, but it takes quite a lot of time maintaining/updating it.

And there's [cookiecutter-django](https://github.com/pydanny/cookiecutter-django). It's awesome project, that let you start your project with quite a few so-called best practices. It also comes with a few commonly used components that help speed up your development.

## Virtualenv
If you’ve gone through a few python docs, you surely already see this. I can't recommend it enough.

Always use [virtualenv](https://virtualenv.pypa.io/en/stable/) to separate environments between projects. Even if you have only 1 project to start with, it help not to cluster global, and you will soon have more projects.

You can specify python version when you start a new environment:

`virtualenv env -p python3`

And make sure to check out [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/) as well, since it helps manage different virtual environments with ease:

- Have all the virtual environments in one single place
- Get in virtual environments quickly, for example just run  `workon awesome project` from anywhere, and you're in.
- Set up scripts to run when you get in/out of the environments (simple example: change to project directory, boot up some stuff)


## Settings structure
This is another big deal thing. Seriously.

Normal development workflow would be something like this, you do development locally, then push it to some sort of staging server, and finally, live server.

Each environment has its own settings and configuration (database configuration would be different from local to production for example).

For certain things, especially sensitive information, getting it from environment variables would be an option.

For others, you can set different settings file for different environment.

```
Project-folder
- settings
-- base.py
-- local.py
-- staging.py
-- production.py
-- test.py
```

`base.py` would contain the common settings among environments, while `local.py` contains settings specific only to local.
`local.py`, `staging.py` and `production.py` would import `base.py`.
And you can use environment variable to determine which setting file you want to use. Example for `manage.py` (for local running)

```
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'config.settings.local')
```

And you already get this if you make use of cookiecutter-django!


## Custom user model from beginning
Always go for custom user model from the very beginning.

You might think since the project is simple, you don't actually need a custom user model to start with (what I thought as well).

Well, if the project keeps going for a while, the chance is you'll need to introduce additional stuff to user model very soon. And moving user model is not always a fun task to do.


## Sentry for monitoring
Use Sentry for monitoring. Really, it's simple and easy. What do you get?
- Email notification when there's something wrong with your site.
- Manage your issues (tick things off haha)
- Statics on issues.

## A few apps to use
- [Django-extensions](https://github.com/django-extensions/django-extensions): it has tons of stuff, and I don't use them all. Some are
	- runserver_plus: used to run server locally, instead of normal runserver. You'll get nice debug UI, where you have interactive python shell at each step! (This is the biggest selling point for me)
	- show_urls: show all urls of the projects, and which views they're pointing to.

- [django-debug-toolbar](https://github.com/jazzband/django-debug-toolbar): debug toolbar that you'll show you quite a lot of stuff, like debug messages, which SQL queries are executed.
- [django_builder](https://github.com/mmcardle/django_builder): you just need to put in your models, then it'll generate everything, yes, everything for you, from urls, views, forms, test....