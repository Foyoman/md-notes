```bash
django-admin startproject django_project
python3 manage.py runserver
python3 manage.py startapp blog
```

project level urls > app level views > app level urls 
views > templates
project settings > installed apps

code blocks
views - context
content

```shell
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py createsuperuser
```

```shell
pip install python-decouple
```

```python
last_modified = models.DateTimeField(auto_add=True)
date_posted = models.DateTimeField(auto_add_now=True)
date_posted = models.DateTimeField(default=timezone.now)
```

```shell
python3 manage.py shell
```

`admin.py`
register models for admin

```shell
pip install -r requirements.txt
```

```shell
python3 manage.py startapp users
```

views > form 
`forms.py`

```python
user = models.OneToOneField(User, on_delete=models.CASCADE) 
```

```python
admin.site.register(Profile)
```

```python
class ProfileUpdateForm(forms.ModelForm):
	class Meta:
		model = Profile
		field = ['image']
```

```python
import json
from blog.models import Post
with open('posts.json') as f:
	posts_json = json.load()

for post in posts_json:
	post = Post(title=post['title'], content=post['content'], author_id=post['user_id'])
	post.save()
```