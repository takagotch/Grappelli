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


```

```sh
python manage.py customdashboard
python manage.py customdashboard somefile.py
python manager.py customdashboard projdir/somefile.py


```

```
```


