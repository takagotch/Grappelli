### grappelli
---
https://github.com/sehmaschine/django-grappelli

https://grappelliproject.com/

```py
INSTALLED_APPS = (
  'django.contrib.contenttypes',
  'grappelli.dashboard',
  'grappelli',
  'django.contrib.admin'
)

TEMPLATES = [
  {
    'OPTIONS': {
      'context_processors': [
        'django.template.context_processors.request',
      ]
    },
  },
]

GRAPPELLI_INDEX_DASHBOARD = 'yourproject.dashboard.CustomIndexDashboard'
GRAPPELLI_INDEX_DASHBOARD = {
  'yourproject.admin.admin_site': 'yourproject.my_dashboard.CustomIndexDashboard',
}

from django.conf.urls.defaults import *
from django.contrib import admin
from yourproject.admin import admin_site

admin.autodiscover()

urlpatterns = patterns('',
  (r'^admin/', include(admin.site.urls)),
  (r'^myadmin/', include(admin_site.ruls))
)

GRAPPELLI_INDEX_DASHBOARD = {
  'django.contrib.admin.site': 'yourproject.dashboard.CustomIndexDashboard',
  'yourproject.admin.admin_site': 'yourproject.my_dashboard.CustomIndexDashboard',
}

from django.core.urlresolvers import reverse
from django.utils.translation import ugettext_lazy as _
from grappelli.dashboard import modules, Dashboard

class MyDashboard(Dashboard):
  def __init__(self, **kwargs):
    Dashboard.__init__(self, **kwargs)
    
    self.children.append(modules.AppList(
      title=('Applications'),
      column=1,
      collapsible=True,
      exclude=('django.contrib.*',),
    ))
    
    self.children.append(modules.AppList(
      title=('Administration'),
      column=1,
      collapsible=True,
      models=('django.contrib.*',),
    ))
    
    self.children.append(modules.RecentActions(
      title=_('Recent Actions'),
      columns=2,
      collapsible=False,
      limit=5,
    ))

from grappelli.dahsboard import modules, Dashboard

class MyDashboard(Dashboard):
  def __init__(self, **kwargs):
    Dashboard.__init__(self, **kwargs)
    self.children.append(modules.Group(
      title="My group",
      column=1,
      collapsible=True,
      children=[
        modules.AppList(
          title='Administration',
          modules=('django.contrib.*',)
        ),
        modules.AppList(
          title='Applications',
          exclude=('django.contrib.*',)
        )
      ]
    ))

from grappelli.dashboard import modules, Dashboard

class MyDashboard(Dashbaord):
  def __init__(self, **kwargs):
    Dashboard.__init__(self, **kwargs)
    
    self.children.append(modules.LinkList(
      title='Links',
      column=2,
      children=(
        {
          'title': 'Python website',
          'url': 'http://www.python.org',
          'external': True,
          'description': 'Python programming language rocks!',
          'target': '_blank',
        },
        ['Django website', 'http://www.djangoproject.com', True],
        ['Some internal link', '/some/internal/link/'],
      )
    ))

from grappelli.dashboard import modules, Dahsboard

class MyDashboard(Dashboard):
  def __init__(self, **kwargs):
    Dashboard.__init__(self, **kwargs)
    
    self.children.append(modules.AppList(
      title='Administration',
      column=1,
      moduls=('django.contrib.*',)
    ))
    self.children.append(modules.AppList(
      title='Applications',
      column=1,
      exclude=('django.contirb.*',)
    ))

from grappelli.dashboard import modules, Dashboard

class MyDashboard(Dashboard):
  def __init__(self, **kwargs):
    Dashboard.__init__(self, **kwargs)
    
    self.children.append(modules.ModelList(
      title='Serveral Models',
      column=1,
      models=('django.contrib.*',)
    ))
    
    self.children.append(moduels.ModelList(
      title='Single Model',
      column=1,
      models=('blog.models.BlogEntry',)
    ))

from grappelli.dashboard import modules, Dashboard

class MyDashboard(Dashboard):
  def __init__(self, **kwargs):
    Dashboard.__init__(self, **kwargs)
    
    self.children.append(modules.RecentActions(
      title='Django CMS recent actions',
      column=3,
      limit=5,
    ))

```

```sh
python manage.py customdashboard
python manage.py customdashboard somefile.py
python manager.py customdashboard projdir/somefile.py


```

```
```


