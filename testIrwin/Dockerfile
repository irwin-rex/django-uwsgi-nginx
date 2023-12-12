# Use an official Python runtime as the base image
FROM python:3.10-bullseye

# Set the working directory
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Remove current pip version from python image
RUN rm -rvf /usr/local/lib/python3.10/site-packages/pip-23.0.1.dist-info

# Upgrade pip to a specific version
RUN pip install --upgrade pip==23.3

# Install the requirements
RUN pip install -r requirements.txt

# Copy the rest of the application code into the container
COPY . /app
#COPY uwsgi.ini /var/www/uwsgi.ini

#Collect Static Files
# RUN python manage.py collectstatic

# Expose port 8000 for the Django app
EXPOSE 7000
#RUN python manage.py makemigrations && python manage.py migrate

# Start the application
CMD ["uwsgi", "--ini", "/app/uwsgi.ini"]
# CMD ["python", "manage.py", "runserver", "0.0.0.0:7000"]