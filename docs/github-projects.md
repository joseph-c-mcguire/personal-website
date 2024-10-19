---
layout: page
title: GitHub Projects
permalink: /github-projects/
description: Examples of my GitHub Projects.
---

# GitHub Projects

## [Desktop-Reminders](https://github.com/joseph-c-mcguire/desktop-reminders)
### Description
This is a super simple script that allows you to get reminders on your desktop.

### How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/joseph-c-mcguire/desktop-reminders.git
   cd desktop-reminders
   ```
2. Run the script:
   ```sh
   python3 main.py -c <PATH TO CONFIG FILE>
   ```
   Or just run with the default config found in the repo:
   ```sh
   python3 main.py
   ```

### Configuration
To modify the config, edit the message in the following format:
```
<MESSAGE ID>
  wait: <TIME TO WAIT BETWEEN NOTIFICATIONS>
  message: <THE BODY OF THE NOTIFICATION>
  title: <THE TITLE OF THE NOTIFICATION>
  max-number: <THE MAXIMUM NUMBER OF TIMES THE NOTIFICATION WILL BE POSTED>
```
Additionally, supports extra parameters as supported by [notify-py](https://ms7m.github.io/notify-py/).

---

## [This Website](https://github.com/joseph-c-mcguire/joseph-c-mcguire.github.io)
### Description
The source code for my personal website, built using Jekyll and hosted on GitHub Pages.

### Features
- Responsive design
- Blog posts
- Project showcase
- Contact form

### How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/joseph-c-mcguire/joseph-c-mcguire.github.io.git
   cd joseph-c-mcguire.github.io
   ```
2. Install dependencies:
   ```sh
   bundle install
   ```
3. Run the site locally:
   ```sh
   bundle exec jekyll serve
   ```
4. Open your browser and go to `http://localhost:4000`.

---

## [Murphy's Machine Learning Notes](https://github.com/joseph-c-mcguire/Machine-Learning-Notes)
### Description
A repository for my notebooks as I work through [Murphy's Machine Learning: A Probabilistic Perspective](https://www.amazon.com/Machine-Learning-Probabilistic-Perspective-Computation/dp/0262018020/ref=sr_1_1?keywords=machine+learning+a+probabilistic+perspective&amp;qid=1662569955&amp;sprefix=machine+learning%3A+A+P%2Caps%2C184&amp;sr=8-1).

### How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/joseph-c-mcguire/Machine-Learning-Notes.git
   cd Machine-Learning-Notes
   ```
2. Open the notebooks using Jupyter Notebook or JupyterLab:
   ```sh
   jupyter notebook
   ```

---

## [Math of Data Science Course Material](https://github.com/joseph-c-mcguire/Math-of-data-science)
### Description
Course materials and notes for the Math of Data Science course.

### How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/joseph-c-mcguire/Math-of-data-science.git
   cd Math-of-data-science
   ```
2. Open the materials using Jupyter Notebook or JupyterLab:
   ```sh
   jupyter notebook
   ```

Feel free to explore the repositories and contribute if you find something interesting!