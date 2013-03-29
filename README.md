Openshift + Django + MySQL
==========================

This is a modified version of the original "openshift/django-example" provided by openshift, so it uses the MySQL database instead of SQLite. You can view the original example code here:
https://github.com/openshift/django-example

Run this code on openshift:
---------------------------

Create a python-2.6 application

    rhc app create -a django -t python-2.6

Add the MySQL cartridge.

    rhc cartridge add mysql-5.1 -a django 

Add this upstream repo

    cd django
    git remote add upstream -m master git://github.com/rugebiker/openshift-django-mysql.git
    git pull -s recursive -X theirs upstream master

Then push the repo upstream
    
    git push

Now you should be able to checkout your site

    http://django-$yournamespace.rhcloud.com

To create the admin user and password, access via SSH to your repo on openshift. You can check your SSH info by doing

    rhc domain

When you are logged in to the server, do this

    python-2.6/virtenv/bin/python app-root/repo/wsgi/openshift/manage.py createsuperuser

And write the info it asks you for, and that's it (:

If you have any issues you can contact me at rguerra.marin@gmail.com

Buena suerte!
