1. Create a direcory named "proj".

2. Open terminal and go to directory "proj" by using the following command:
	cd proj

3. I have used django framework for the project. One needs to first install django for this. After then type the following command:
	django-admin startproject mysite
	cd mysite
	chmod u+rwx manage.py                                            (#for permission#)
	./manage.py syncdb
	./manage.py runserver

4. Now type the following command to create you webapplication(I have named it personal):
	python manage.py startapp personal

5. Go to mysite directory (in mysite) and then update the settings.py file. In INSTALLED_APPS add 'personal', save it and its done.

6. Now open urls.py file and update:
from django.conf.urls import url, include
from django.contrib import admin
urlpatterns=[
	url(r'^admin/', admin.site.urls),
	url(r'^$', include('personal.urls')),
] 
Save it.

7. Now go to 'personal' directory and create a urls.py file and update:
from django.conf.urls import url, include
from . import views
urlpatterns = [
	url(r'^$', views.index, name='index'),
]
Save it.

8. Now open views.py from the same directory and update it:
from django.shortcuts import render

def index(request):
	return render(request, 'personal/home.html')
Save it.

9. Create another directory 'templates' in personal. You can put your html files here, django will find them. If you have two templates with the identical name that can be a problem. So to remove this create another directory in 'templates', 'personal'.

10. In personal create and store your html files here. I have already stored a header.html file. I have used Jinja templating here in header.html. To fill in gaps  between tags I have created another file home.html(it consists of login and submit) and save it after writing the commands of interest. 

11. Create another directory in 'personal', 'includes'. The reason for this is includes is very short snippets of code. Create an html file, 'signup.html' that consists of your signup page.

12. Now go to proj/mysite and type the following command:
	./manage.py runserver
	Open up the link. And we are done with our webapplication.



To test the code:
If django already installed in your system, then store the 'proj' folder in your home directory and type the following command:
cd proj/mysite
./manage.py runserver
you will get address link: http://127.0.0.1:8000/
just open it and there is the work. 
