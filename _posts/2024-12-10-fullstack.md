---
title: "Full-Stack Example Web Application"
author: Joseph McGuire
date: 2024-12-10
header_image: /assets/images/bishop-peak.png
katex: true
---

# Introduction
So this project started as a way to learn, "How do you build a web application?" 
As a data scientist for several years, and having a background in applied mathematics, I haven't had the oppurtunity to get a hands-on experience of building a fully deployed web application.
I had plenty of experience building machine learning models for various applications, like data anonymization and regression models for time-series predictions, but never had experience on how these models get deployed "in the wild", as it were.
And I always learn best by doing, so my goal for this was to build a simple web application that allowed one to play with a Scikit-Learn based model for a simple models, or set of models.
So this project was a learning experience for me, go into this with less than a caustic wit and I'll be very appreciative as a novice student ;).

As always, I will try to describe this process in an understandable and user-friendly manner; i.e. no buzzwords. 

In this article, I'll layout:
- Architecture
- Backend Design
- Frontend Design
- Deployment

Finally, I'll wrap up with some concluding comments on the overall process.
I hope this is insightful and/or helpful :)

# Architecture

First off, building a full-stack application, you'll need a backend API that handles the serving of the ML model.
This has no GUI, and is just a endpoint that we can query to get information of the model to the frontend, without hosting and building the model in JS (I'm not sure that's even possible).

Secondly, for the backend, we'll need to deploy this backend to a server

1. **Backend**: A REST API, that is built in **Flask** (a Python library) that allows for CURL requests of the services provided. 
In particular, since we're dealing with a front-facing machine learning models and a web application that allows you to explore and mess around with the model, the core functionalities of the application were **predictions** and **diagnostics**; overall serving the model to the user via the REST API.
(I also threw in an additional service: training of the model, but haven't tested this endpoint with the frontend at the time of writing this)
2. **Frontend**: The frontend was by far the messiest part of this whole venture, and by consequence also the biggest learning experience for myself. 
The frontend is built entirely in **React** which is a **Javascript/NodeJS** framework that allows for containerized and compartmentalized web design.
The choice of these libraries mostly boiled down to hearing about React as a simple Javascript tool that allowed you to build compartmentalized apps, so I went ahead with that (in hindsight, I might have looked more into Ruby or Typescript).
The purpose of the fronted for this was to serve the model in a way that emphasizes interactivity and exploration of the model.
With this in mind, I used the really nice **PlotlyJS** framework for many of the plots, as it allowed for a great deal of customizablity and user interactivity.
3. **Deployment**: The choice of deployment platform changed a lot throughout this project. First it was a naive attempt at trying to deploy Docker containers to **AWS** and **Azure**.
I moved past these platforms:
    * (1) because of the platforms cost was prohibitive for my use case (a simple little toy-example)
    * (2) they were difficult to navigate for a newcomer and I found the resources for this use case were lacking for me.

    I landed on using the Salesforce-based software **Heroku**, which provided a much simpler interface for developers, and was priced reasonably enough for my use case of this small little example web application.
    And I ended up dropping the Docker/containerization solution, as **Heroku**, by default, sets up virtual environments with NodeJS and Python environments.
    So long as your dependency files are correct and up-to-date, then you're golden. 
    Additionally, **Heroku** allowed for seamless continuous integration with GitHub, which was my hosting source for the source-code for this project.

4. **Testing**: Testing was an interesting problem in this project. 
First, I had plenty of experience unit-testing with **PyTest** in Python. 
But the end-point and app testing was a completely foreign experience for me.
The mock environments in **PyTest** were a huge help, essentially mock objects that you can define to mimic test data or expected returns from the true function calls.
Secondly, since I was new to NodeJS and Javascript, in general, the unit-testing process was a headache to learn. 

# Backend

The primary purpose of the backend was to handle the serving of machine learning models and provide endpoints for predictions and diagnostics. The backend is built using Flask, a Python web framework, and includes several key components:

- **Model Management**: The backend manages multiple models, including Decision Tree, Gradient Boosting, and Random Forest models. These models are trained on a predictive maintenance dataset from UCI.
- **API Endpoints**: The backend provides various endpoints for interacting with the models, such as retrieving feature importance, confusion matrices, ROC curves, and making predictions.
- **Configuration**: The backend is highly configurable, with settings for model training, data paths, and other parameters defined in a configuration file.
- **Testing**: Unit tests are provided to ensure the functionality of the backend. These tests cover the core logic and API endpoints, ensuring compatibility with the frontend.

## Repository Structure

The backend repository is organized as follows:

```
.github/workflows/
  ci.yml
app/
  models/
    model_manager.py
  routes/
    model_routes.py
  services/
    model_diagnostics.py
  utils/
    helper_functions.py
  __init__.py
  config.py
  extensions.py
data/
models/
scripts/
tests/
.gitignore
LICENSE
Procfile
README.md
app.py
pyproject.toml
requirements.txt
run.py
train_model.yaml
```

### Key Files and Directories

- **app/**: Contains the main application code.
  - **models/**: Handles loading and saving models.
  - **routes/**: Defines the API endpoints.
  - **services/**: Includes the logic for model diagnostics.
  - **utils/**: Contains utility functions used across the application.
  - **config.py**: Handles configuration settings such as file paths and training parameters.
  - **extensions.py**: Adds Flask extensions like CORS.
  - **__init__.py**: Initializes the Flask application.

- **data/**: Contains the processed and raw data files for the project.
- **models/**: Contains the trained models used by the frontend for serving.
- **scripts/**: Contains scripts for tasks such as sample CURL requests.
- **tests/**: Contains unit tests for the repository.
- **Procfile**: Defines the commands to run the application on Heroku.
- **requirements.txt**: Lists the Python dependencies for the project.
- **run.py**: The development server entry point.
- **app.py**: The production server entry point.
- **train_model.yaml**: Configuration file for training models.

## How to Use

To install and run the backend locally, follow these steps:

```bash
git clone https://github.com/joseph-c-mcguire/webapp-example-backend.git
cd webapp-example-backend
pip install -r requirements.txt
python run.py  # For development
python app.py  # For production
```

# Frontend

The frontend of the Predictive Maintenance System is built using React, a popular JavaScript library for building user interfaces. The frontend communicates with the backend to fetch data and display it to the user. Key features of the frontend include:

- **Interactive Design**: The frontend allows users to interact with the models, query them with new inputs, and view performance metrics.
- **Component-Based Architecture**: The application is built using React components, making it modular and easy to maintain.
- **PlotlyJS Integration**: The frontend uses PlotlyJS for creating interactive plots and visualizations, enhancing the user experience.
- **Test-Driven Development**: The frontend is developed using test-driven development practices, with unit tests ensuring the functionality of the components.

To install and run the frontend locally, follow these steps:

```bash
git clone https://github.com/joseph-c-mcguire/webapp-example-frontend.git
cd webapp-example-frontend
npm install
npm start
```

# Deployment

Deploying the full-stack application involves setting up both the frontend and backend on a hosting platform. For this project, Heroku was chosen for its simplicity and integration with GitHub. The deployment process includes:

## Heroku Setup

1. **Create Heroku Apps**: 
   - Sign up for a Heroku account if you don't have one.
   - Install the Heroku CLI from [here](https://devcenter.heroku.com/articles/heroku-cli).
   - Create a new Heroku app for the backend:
     ```bash
     heroku create your-backend-app-name
     ```
   - Create a new Heroku app for the frontend:
     ```bash
     heroku create your-frontend-app-name
     ```

2. **Configure Environment Variables**:
   - Set up necessary environment variables for both apps using the Heroku CLI or the Heroku dashboard.
   - For example, to set an environment variable:
     ```bash
     heroku config:set VARIABLE_NAME=value --app your-app-name
     ```

## Continuous Integration with GitHub

1. **GitHub Actions**:
   - Create a `.github/workflows` directory in your repository.
   - Add a workflow file (e.g., `deploy.yml`) for continuous integration and deployment:
     ```yaml
     name: Deploy to Heroku

     on:
       push:
         branches:
           - main

     jobs:
       build:
         runs-on: ubuntu-latest

         steps:
         - uses: actions/checkout@v2

         - name: Set up Node.js
           uses: actions/setup-node@v2
           with:
             node-version: '14'

         - name: Install dependencies
           run: npm install

         - name: Build
           run: npm run build

         - name: Deploy to Heroku
           env:
             HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
           run: |
             git remote add heroku https://git.heroku.com/your-frontend-app-name.git
             git push heroku main
     ```

2. **Heroku API Key**:
   - Generate a Heroku API key from the Heroku dashboard under Account Settings.
   - Add the API key to your GitHub repository secrets:
     - Go to your repository on GitHub.
     - Click on `Settings` > `Secrets` > `New repository secret`.
     - Add a new secret with the name `HEROKU_API_KEY` and paste your Heroku API key.

## Production Configuration

1. **Backend Configuration**:
   - Ensure that the `Procfile` is set up correctly for the backend:
     ```
     web: python app.py
     ```

2. **Frontend Configuration**:
   - Ensure that the `Procfile` is set up correctly for the frontend:
     ```
     web: npm start
     ```

3. **Deploying**:
   - Push your code to GitHub. The GitHub Actions workflow will automatically deploy your application to Heroku.

# Conclusion

Building a full-stack web application was a valuable learning experience. It provided insights into the challenges of integrating different technologies and the importance of testing and deployment practices. The Predictive Maintenance System serves as a practical example of how to build and deploy a machine learning application, from data processing to model serving and user interaction.

Feel free to explore the repositories and contribute if you find something interesting!

- [Frontend Repository](https://github.com/joseph-c-mcguire/webapp-example-frontend)
- [Backend Repository](https://github.com/joseph-c-mcguire/webapp-example-backend)
- [Deployed Application](https://webapp-example-frontend-56f2ec31cf0a.herokuapp.com/)