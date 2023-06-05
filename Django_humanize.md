# template에서 1000단위(천단위) comma 표시
```python
# settings.py

INSTALLED_APPS = [
  ...
  'django.contrib.humanize',
  ...
]
```
```html
<!-- base.html -->

{% load humanize %}
```

```python
{{ object.price }} 						<!-- 4500 --> 						 
{{ object.price | intcomma }}	<!-- 4,500 -->
```