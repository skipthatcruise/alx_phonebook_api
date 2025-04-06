Main Features
Users must be able to save phone numbers
Search for contacts in the phone book
Edit contacts in the phone book
Delete contacts in the phone book 

Modular Django apps 
Users App: Manages user authentication and profiles.
Contact App: Manages phone book contacts(CRUD operations). 

Core Models and Relationships 
Users App(users/models.py):

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
   #code will be inserted here

Contacts App(contacts/models.py):

from django.db import models
from django.conf import settings

class Contact(models.Model):
    #Model to store phonebook contacts
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE, related_name="contacts")
    name = models.CharField(max_length=255)
    phone_number = models.CharField(max_length=15, unique=True)
    email = models.EmailField(blank=True, null=True)

    def _str_(self):
        return f"{self.name} - {self.phone_number}"


API Endpoints			

HTTP Method
Endpoint
Description
POST
/api/register/
Register a new user
POST
/api/login/
Authenticate user
POST
/api/logout/
Logout user 
GET	
/api/contacts
List all user contacts


POST
/api/contacts/
Add new contacts


GET
/api/contacts/<id>/
Retrieve a contact 
PUT
/api/contacts/<id>/
Update a contact
DELETE
/api/contacts/<id>/
Delete a contact

