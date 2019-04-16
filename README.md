# Django-SQL-server-connection
Use MS SQL server 2017 as backend for Django 2

#### Requirements
- Python 3.7.1
- Django 2.1.7
- pyodbc 4.0.25
- Microsoft SQL Server 2017 

### Installation

Install django and pyodbc driver
```
$pip install Django==2.1.7
$pip install pyodbc==4.0.25
```

### Creating Project

Create project *DjangoSQLServerConnection* using Django-admin

```
$django-admin startproject DjangoSQLServerConnection
```

### Configuration

**Database:** create database in SQL server with name *DjangoSQLServerTest*
**settings.py** Once the project is created open *settings.py* file in sub directory same as project name *DjangoSQLServerConnection*

in *settings.py* update the **DATABASES** session(dictonary) as follows

```
DATABASES = {
    'default': {
        'ENGINE': 'sql_server.pyodbc',
        'HOST': 'DESKTOP-R3PHQ32', #Server Name or IP
        'USER': 'dbusername', #SQL Server Authentication UserName
        'PASSWORD': 'dbpassword', #SQL Server Authentication Password
        'NAME': 'DjangoSQLServerTest', #Database Name
        'OPTIONS':{
            'driver': 'ODBC Driver 13 for SQL Server'
        }
    }
}
```

### Apply migrations

```
$cd DjangoSQLServerConnection
DjangoSQLServerConnection$ python manage.py migrate
```
if you can see below result, the migrations are completed and the connection to SQL server is established. 

```
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK
```
You can see below list of tables created in SQL server database *DjangoSQLServerTest*

- django_migrations
- django_content_type
- auth_permission
- auth_group
- auth_group_permissions
- auth_user
- auth_user_groups
- auth_user_user_permissions
- django_admin_log
- django_session
