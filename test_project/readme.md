# Introduction
Aldryn_newsblog gets all plugins inside article content placeholder and renders them programatically. 
As they are rendered application clears content from html tags and adds it to field 'search_data' of Article model.

# The problem
To render a plugin the application actually simulates circumstances to render it. 
So they need a request and its context. 
**But aldryn_newsblog uses default context without any processing according to our settings.** In this case, all plugins which depend on our context processors, which add additional info to context, just cant be rendered.

# To see the bug 
_(using aldryn_newsblog v. 2.1.1):_

1. In application settings enable search data upadting with: `ALDRYN_NEWSBLOG_UPDATE_SEARCH_DATA_ON_SAVE = True`
1. Create an article.
1. Add Google maps plugin (it`s template using sekizai tags)
1. Try to save.

# In current project
1. This repository already has enabled `ALDRYN_NEWSBLOG_UPDATE_SEARCH_DATA_ON_SAVE` and has an article with Google maps plugin.
1. Just create a superuser via `python manage.py createsuperuser`
1. Move to article (`http://localhost:8000/en/article/`)
1. Open Google Map plugin and try to save it.
