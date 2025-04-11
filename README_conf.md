# Django MongoDB Integration

This project demonstrates how to integrate Django with MongoDB using djongo as the connector.

## Setup Instructions

### Prerequisites
- Python 3.x
- MongoDB Atlas account (or local MongoDB instance)
- Git (optional)

### Environment Setup

1. Create and activate a virtual environment
   ```bash
   python -m venv venv
   venv\Scripts\activate  # On Windows
   # source venv/bin/activate  # On macOS/Linux
   ```

2. Install required packages
   ```bash
   pip install django==3.2.20
   pip install djongo==1.3.6
   pip install pymongo==3.11.4
   pip install sqlparse==0.2.4
   pip install python-dotenv
   pip install dnspython
   ```

3. Create a Django project
   ```bash
   django-admin startproject data_pipeline_mongodb
   cd data_pipeline_mongodb
   ```

### Configuration

1. Create a `.env` file in the project root:
   ```
   # MongoDB Connection - Atlas
   MONGO_URI=mongodb+srv://username:password@healthcentercluster.4v2d6.mongodb.net/?retryWrites=true&w=majority&appName=HealthCenterCluster
   MONGO_DB=DataAutomationProcessingHealthCenterDB
   ```
   *Replace username and password with your actual MongoDB credentials*

2. Configure Django settings (`settings.py`):
   ```python
   import os
   from dotenv import load_dotenv
   
   # Load environment variables
   load_dotenv()
   
   # MongoDB connection
   DATABASES = {
       'default': {
           'ENGINE': 'djongo',
           'NAME': os.getenv('MONGO_DB'),
           'ENFORCE_SCHEMA': False,
           'CLIENT': {
               'host': os.getenv('MONGO_URI'),
           },
       }
   }
   ```

### Running the Application

1. Run migrations
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

2. Start the development server
   ```bash
   python manage.py runserver
   ```

## Troubleshooting

### Version Compatibility
Ensure you're using compatible versions:
- Django: 2.1 to 3.2.x
- djongo: 1.3.6
- pymongo: 3.11.4
- sqlparse: 0.2.4

### Common Errors

1. **Connection Error**
   - Check MongoDB Atlas network access settings
   - Verify credentials in your `.env` file
   - Ensure proper network connectivity

2. **Dependency Conflicts**
   ```
   pip uninstall django djongo pymongo sqlparse
   pip install django==3.2.20 djongo==1.3.6 pymongo==3.11.4 sqlparse==0.2.4
   ```

3. **Authentication Error**
   - Ensure your MongoDB Atlas user has the correct permissions
   - Check if your database name is correct

## Project Structure

```
data_pipeline_mongodb/
├── .env                    # Environment variables
├── manage.py
├── venv/                   # Virtual environment
└── data_pipeline_mongodb/
    ├── __init__.py
    ├── asgi.py
    ├── settings.py         # Contains MongoDB configuration
    ├── urls.py
    └── wsgi.py
```

## License
MIT License

Copyright (c) 2025 Eric Maniraguha

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Contact
Eric Maniraguha  
GitHub: [ericmaniraguha](https://github.com/ericmaniraguha)  
Email:  
LinkedIn: [ericmaniraguha](https://www.linkedin.com/in/ericmaniraguha/)