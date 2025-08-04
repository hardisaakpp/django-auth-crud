# Django Auth CRUD - Task Management System

A complete Django web application for task management with user authentication, featuring a full CRUD (Create, Read, Update, Delete) interface for managing personal tasks.

## 🚀 Features

- **User Authentication**: Sign up, sign in, and logout functionality
- **Task Management**: Create, read, update, and delete tasks
- **Task Organization**: Mark tasks as important and complete
- **User-specific Tasks**: Each user can only see and manage their own tasks
- **Responsive Design**: Clean and modern user interface
- **Production Ready**: Configured for deployment on Render.com

## 🛠️ Technologies Used

- **Backend**: Django 5.0.6
- **Database**: SQLite (development) / PostgreSQL (production)
- **Authentication**: Django's built-in authentication system
- **Deployment**: Render.com with automatic builds
- **Static Files**: WhiteNoise for static file serving

## 📋 Prerequisites

- Python 3.8 or higher
- pip (Python package installer)
- Git

## 🔧 Installation

### 1. Clone the repository
```bash
git clone <repository-url>
cd django-auth-crud
```

### 2. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run database migrations
```bash
python manage.py migrate
```

### 5. Create a superuser (optional)
```bash
python manage.py createsuperuser
```

### 6. Run the development server
```bash
python manage.py runserver
```

The application will be available at `http://127.0.0.1:8000/`

## 📖 Usage

### Authentication
- **Sign Up**: Create a new account at `/signup/`
- **Sign In**: Log in to your account at `/signin/`
- **Logout**: Log out from your account at `/logout/`

### Task Management
- **View Tasks**: See all your pending tasks at `/tasks/`
- **Create Task**: Add a new task at `/tasks/create/`
- **Edit Task**: Modify existing tasks at `/tasks/<task_id>/`
- **Complete Task**: Mark tasks as completed
- **Delete Task**: Remove tasks from your list
- **Completed Tasks**: View completed tasks at `/tasks_completed/`

### Task Features
- **Title**: Required field for task name
- **Description**: Optional detailed description
- **Important**: Mark tasks as high priority
- **Created Date**: Automatically tracked
- **Completed Date**: Set when task is marked as complete

## 🗄️ Database Models

### Task Model
```python
class Task(models.Model):
    title = models.CharField(max_length=100)
    description = models.TextField(blank=True)
    created = models.DateTimeField(auto_now_add=True)
    datecompleted = models.DateTimeField(null=True, blank=True)
    important = models.BooleanField(default=False)
    user = models.ForeignKey(User, on_delete=models.CASCADE)
```

## 🌐 URL Structure

| URL Pattern | View | Description |
|-------------|------|-------------|
| `/` | home | Landing page |
| `/signup/` | signup | User registration |
| `/signin/` | signin | User login |
| `/logout/` | signout | User logout |
| `/tasks/` | tasks | View pending tasks |
| `/tasks_completed/` | tasks_completed | View completed tasks |
| `/tasks/create/` | create_task | Create new task |
| `/tasks/<id>/` | task_detail | View/edit specific task |
| `/tasks/<id>/complete` | complete_task | Mark task as complete |
| `/tasks/<id>/delete` | delete_task | Delete task |
| `/admin/` | admin | Django admin interface |

## 🚀 Deployment

This project is configured for deployment on Render.com with the following setup:

### Environment Variables
- `SECRET_KEY`: Django secret key
- `DATABASE_URL`: PostgreSQL connection string (automatically set by Render)

### Build Process
The `build.sh` script handles:
1. Installing dependencies
2. Collecting static files
3. Running database migrations

### Local Development vs Production
- **Development**: Uses SQLite database
- **Production**: Uses PostgreSQL database (configured via `dj-database-url`)

## 📁 Project Structure

```
django-auth-crud/
├── djangocrud/          # Main Django project
│   ├── settings.py      # Project settings
│   ├── urls.py          # Main URL configuration
│   └── wsgi.py          # WSGI configuration
├── tasks/               # Tasks app
│   ├── models.py        # Task model
│   ├── views.py         # View functions
│   ├── forms.py         # Task form
│   ├── admin.py         # Admin configuration
│   └── templates/       # HTML templates
├── requirements.txt      # Python dependencies
├── build.sh            # Deployment script
└── manage.py           # Django management script
```

## 🔒 Security Features

- **User Authentication**: Login required for all task operations
- **User Isolation**: Users can only access their own tasks
- **CSRF Protection**: Built-in Django CSRF protection
- **SQL Injection Protection**: Django ORM prevents SQL injection
- **XSS Protection**: Django template system prevents XSS attacks

## 🧪 Testing

Run the test suite:
```bash
python manage.py test
```

## 📝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Support

If you have any questions or need help with the project, please open an issue on GitHub.

---

**Happy Task Managing!** 🎉 