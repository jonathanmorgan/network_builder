network_builder
===============

Django network_builder application, models to build and persist network data - nodes and ties of multiple types with attribute data.

This is going to be great.  More details to come.

Installing network_builder
==========================

To install:

Django:
-------

* install and configure django to talk with a database (http://docs.djangoproject.com/en/dev/intro/tutorial01/).

* install and configure a django application named "research" (including setting up database in settings.py).

    * In the folder where you want your application, run:
    
			django-admin.py startproject research

    * This creates the following folder structure and files (among others):

        	/research

            	manage.py

            	/research

                	settings.py
    
    * Edit the research/research/settings.py file and update it with details of your database configuration (https://docs.djangoproject.com/en/dev/intro/tutorial01/#database-setup).

* install and configure the network_builder application.

    * move network_builder into your django application directory.  Relatively speaking, based on the directory structure above, this would mean placing the network_builder folder, either cloned from git:
        
        	git clone git@github.com:jonathanmorgan/network_builder.git
        
    or copied from elsewhere, into the research folder, alongside manage.py and the second research/research folder.
        
    * add network_builder to your settings.py file's list of applications.  Based on file structure above, you'd add the following line:

    	    'network_builder',  

    to the python list stored in INSTALLED_APPS.

    * initialize the database - go into directory where manage.py is installed, and run "python manage.py syncdb".

    * configure your web server so it knows of your wsgi.py file.  If apache, need to make sure mod_wsgi is installed, add something like this to the apache config, in the Virtual Host you want to host the django application:
    
    		WSGIDaemonProcess sourcenet-1 threads=10 display-name=%{GROUP}
    		WSGIProcessGroup sourcenet-1
    		WSGIScriptAlias /sourcenet <path_to_django_app>/<app_name>/<app_name>/wsgi.py
    
* play (and hope it doesn't break!).