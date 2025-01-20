# fullstack

Sure! Here's a step-by-step guide to quickly create and start multiple projects using **Vite** for frontend and **Django** for backend. I’ll walk you through the commands for setting up each project type and give you a smooth, fast starting process for each.

### **1. Setting up Frontend with Vite (React or Angular)**

#### **For React Project with Vite:**

1. **Create the React Project with Vite**:
   To create a new Vite project with React, use the following command:

   ```bash
   npm create vite@latest react-project --template react
   ```

   This will create a folder named `react-project` with all the necessary files for a Vite-React project.

2. **Navigate into the project directory**:

   ```bash
   cd react-project
   ```

3. **Install Dependencies**:

   Install all required dependencies by running:

   ```bash
   npm install
   ```

4. **Start the Development Server**:

   Finally, start the development server:

   ```bash
   npm run dev
   ```

   This will start the Vite development server, and you can access the React project at `http://localhost:3000`.

---

#### **For Angular Project (with Vite as build tool)**:

Though Angular does not officially use Vite (it uses Angular CLI by default), you can still configure Vite with Angular or use it for a custom build setup.

To quickly get started with Angular, it's easiest to use the Angular CLI:

1. **Install Angular CLI (if you don't have it already)**:
   
   ```bash
   npm install -g @angular/cli
   ```

2. **Create a New Angular Project**:

   ```bash
   ng new angular-project --routing --style=scss
   ```

3. **Navigate to the Project Directory**:

   ```bash
   cd angular-project
   ```

4. **Install Dependencies** (this is done automatically when creating the Angular project).

5. **Serve the Angular Application**:

   ```bash
   ng serve
   ```

   Your Angular app will be available at `http://localhost:4200`.

---

### **2. Setting Up the Backend with Django**

1. **Create and Set Up the Django Project**:

   If you don't have Django installed, first install it:

   ```bash
   pip install django
   ```

2. **Create a New Django Project**:

   To create a new Django project, run:

   ```bash
   django-admin startproject backend-project
   ```

3. **Navigate to the Backend Project**:

   ```bash
   cd backend-project
   ```

4. **Create a Django App**:

   For your app (e.g., `main`), run:

   ```bash
   python manage.py startapp main
   ```

5. **Install Django Rest Framework** (if you want to use Django for API development):

   ```bash
   pip install djangorestframework
   ```

6. **Set Up Django Database** (run migrations):

   ```bash
   python manage.py migrate
   ```

7. **Run the Django Development Server**:

   Now you can run the server:

   ```bash
   python manage.py runserver
   ```

   This will start the backend server, and the Django app will be available at `http://127.0.0.1:8000`.

---

### **3. Connect the Frontend and Backend (Optional)**

Once you have both your frontend (React/Angular) and backend (Django) running, you might want to connect them.

- **Django REST API (for React or Angular)**: If you're building a full-stack app, you can set up Django REST Framework to serve APIs that your frontend will consume. You can add views, serializers, and routes to expose your data as API endpoints.

---

### **4. Optional: Dockerize the Projects (if needed)**

If you want to containerize both the React/Angular frontend and Django backend, here's a basic setup for **Docker**:

#### **For React (or Angular) + Django:**

1. **Dockerfile for React/Angular**:

   In the root of your frontend project (e.g., `react-project` or `angular-project`), create a `Dockerfile`:

   ```Dockerfile
   # Use official Node.js image as the base image
   FROM node:16

   # Set working directory
   WORKDIR /app

   # Install dependencies
   COPY package.json package-lock.json ./
   RUN npm install

   # Copy all files
   COPY . .

   # Expose port and run the app
   EXPOSE 3000
   CMD ["npm", "run", "dev"]
   ```

2. **Dockerfile for Django**:

   In your `backend-project` directory, create a `Dockerfile`:

   ```Dockerfile
   # Use official Python image as the base image
   FROM python:3.9

   # Set working directory
   WORKDIR /app

   # Install dependencies
   COPY requirements.txt ./
   RUN pip install -r requirements.txt

   # Copy the project files
   COPY . .

   # Expose the port Django uses
   EXPOSE 8000

   # Start Django app
   CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
   ```

3. **docker-compose.yml** (Optional, to run both frontend and backend together):

   If you're using **Docker Compose** to run both the frontend and backend services together:

   ```yaml
   version: '3'
   services:
     frontend:
       build:
         context: ./react-project  # or angular-project
       ports:
         - "3000:3000"
     backend:
       build:
         context: ./backend-project
       ports:
         - "8000:8000"
   ```

4. **Build and Run with Docker Compose**:

   ```bash
   docker-compose up --build
   ```

This will start both the frontend (React or Angular) and backend (Django) in separate containers, and they will be accessible at the following URLs:

- Frontend: `http://localhost:3000`
- Backend: `http://localhost:8000`

---

### **5. Recap of Commands to Start Each Project:**

1. **Vite with React**:
   ```bash
   npm create vite@latest react-project --template react
   cd react-project
   npm install
   npm run dev
   ```

2. **Vite with Angular (via Angular CLI)**:
   ```bash
   npm install -g @angular/cli
   ng new angular-project --routing --style=scss
   cd angular-project
   ng serve
   ```

3. **Django Backend**:
   ```bash
   pip install django
   django-admin startproject backend-project
   cd backend-project
   python manage.py migrate
   python manage.py runserver
   ```

4. **Django + React/Angular Connection** (optional): Set up Django Rest Framework for API routes and connect them to your React or Angular frontend.

---

### **Conclusion:**

This guide should help you quickly set up both frontend and backend projects using **Vite** for fast React/Angular development and **Django** for backend development. The use of Docker Compose (optional) makes it even easier to manage both services in one setup.