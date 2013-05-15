network_builder
===============

Django network_builder application, models to build and persist network data - nodes and ties of multiple types with attribute data.

This is going to be great.  More details to come.

Installing network_builder
==========================

To install:

Django:
-------

* before you do anything else, if you aren't familiar with django, it is good to just run through the django tutorial, to get an idea how it all works, what it takes to configure django to talk with a database (http://docs.djangoproject.com/en/dev/intro/tutorial01/).

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

    * initialize the database - Once you either make a fresh install and configure settings.py or install the application in an existing django install, go into directory where manage.py is installed, and run "python manage.py syncdb".

    * configure your web server so it knows of your wsgi.py file.  If apache, need to make sure mod_wsgi is installed, add something like this to the apache config, in the Virtual Host you want to host the django application:

    		WSGIDaemonProcess sourcenet-1 threads=10 display-name=%{GROUP}
    		WSGIProcessGroup sourcenet-1
    		WSGIScriptAlias /sourcenet <path_to_django_app>/<app_name>/<app_name>/wsgi.py

* play (and hope it doesn't break!).

Using Network Builder
=====================

For now, just have classes/models that hold network information pre-query.

Configuration
-------------

* use manage.py to load the attribute types fixtures:

    python manage.py loaddata attribute_type.json

* use manage.py to load the attribute derivation types fixtures:

    python manage.py loaddata attribute_derivation_type.json

* if you want them, create node types and/or tie types.

* play (and hope it doesn't break!).  By play, I mean build programs that create nodes, associate attributes to them, and create ties of multiple types between them, then use that data for network analysis!  Eventually, planning on building an output framework so that networks in this database can be easily output to common file formats for social network analysis.  For now, though, you'll have to write your output yourself.

* to include the network builder classes in another program, you'll need to import the classes.  For example, to use nodes, node types, ties, and tie types, after making sure that the network_builder packages is in your python path, you'd include the following imports in your python source file:

    # THEREPOOFDOOM network classes, for building messaging networks for users.
    from network_builder.models import Node
    from network_builder.models import Node_Type
    from network_builder.models import Tie
    from network_builder.models import Tie_Type

    OR, you could just import the network_builder package if you want to maintain namespace separation (in case you have a Node class already, for example):

    import network_builder

    THEN reference:

    network_builder.models.Node()

    to create a Node instance, etc.

## License

Copyright 2011-2013 Jonathan Morgan

This file is part of [http://github.com/jonathanmorgan/network_builder](http://github.com/jonathanmorgan/network_builder).

network_builder is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

network_builder is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with [http://github.com/jonathanmorgan/network_builder](http://github.com/jonathanmorgan/network_builder).  If not, see
[http://www.gnu.org/licenses/](http://www.gnu.org/licenses/).