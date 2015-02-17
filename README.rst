######
README
######

install package
===============

pip install git+git://github.com/COEXCZ/django-translation-manager.git

add 'translation_manager' to settings.py: INSTALLED_APPS

add variables from https://bitbucket.org/coex/translation_manager/src/master/translation_manager/app.settings.py?at=master to settings.py

add post_save signal to restart server:

.. code-block:: python
    :linenos:

    from translation_manager.signals import post_save as translation_post_save
    
    translation_post_save.connect(restart_server, sender=None)


syncdb 
======

    ./manage.py syncdb

or migrate:

    ./manage.py migrate


load strings from po files
==========================


    ./manage.py shell
    
    from translation_manager.manager import Manager
    
    m = Manager()
    m.load_data_from_po()
    

optional: add link to translation admin
=======================================

{% url admin:translation_manager_translationentry_changelist %}


Known bugs:
===========

If you are using different base site you have to register admin to your site.


License note:
=============


Commercial license is being prepared. Please contact us for details at info@coex.cz.