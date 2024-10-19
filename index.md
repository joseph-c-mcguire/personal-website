---
layout: page
title: Home
---

<!-- Link to Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

<style>
  body {
    font-family: 'Roboto', sans-serif;
    margin: 0;
    padding: 0;
  }
  .header {
    position: relative;
    background-image: url('images/bishop-peak.png');
    background-size: cover;
    background-position: center;
    padding: 100px 0;
    text-align: center;
    color: #fff;
  }
  .header::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5); /* Semi-transparent overlay */
    z-index: 1;
  }
  .header-content {
    position: relative;
    z-index: 2;
  }
  .header-image {
    border-radius: 50%;
    width: 150px;
    height: 150px;
    object-fit: cover;
    display: block;
    margin: 0 auto 20px;
    border: 5px solid #fff;
  }
  .welcome-text {
    font-family: 'Roboto', sans-serif;
    color: #fff;
    margin: 0;
  }
  .welcome-text h1 {
    font-size: 2.5em;
    color: #fff;
    margin-bottom: 10px;
  }
  .welcome-text p {
    font-size: 1.2em;
    margin-top: 0;
  }
  .latest-posts, .github-projects, .technical-writing, .blog-posts {
    font-family: 'Roboto', sans-serif;
    color: #555;
    padding: 20px;
  }
  .resume-section {
    font-family: 'Roboto', sans-serif;
    color: #333;
    margin: 20px 0;
    padding: 20px;
  }
  .resume-section h2 {
    color: #555;
    margin-bottom: 10px;
  }
  .resume-section ul {
    list-style-type: none;
    padding: 0;
  }
  .resume-section ul li {
    margin: 5px 0;
  }
  .end-text {
    font-family: 'Roboto', sans-serif;
    color: #555;
    margin: 0;
  }
</style>

<div class="header">
  <div class="header-content">
    <img src="images/headshot.jpg" alt="Joseph McGuire" class="header-image">
    <div class="welcome-text">
      <h1>Joseph McGuire</h1>
      <p>Research Engineer | AI/ML Enthusiast</p>
    </div>
  </div>
</div>

<div class="latest-posts">
  <h2>Latest Posts</h2>
  <ul>
    {% for post in site.posts limit:5 %}
      <li><a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}</li>
    {% endfor %}
  </ul>
</div>

<div class="resume-section">
  <h2>Contact</h2>
  <ul>
    <li>Phone: +1(805)468-5639</li>
    <li>Location: Providence, RI 02906</li>
    <li>Email: <a href="mailto:joseph.c.mcg@gmail.com">joseph.c.mcg@gmail.com</a></li>
    <li>GitHub: <a href="https://github.com/joseph-c-mcguire">joseph-c-mcguire</a></li>
    <li>LinkedIn: <a href="https://www.linkedin.com/in/joseph-c-mcg">joseph-c-mcg</a></li>
    <li>Website: <a href="https://joseph-c-mcguire.github.io">joseph-c-mcguire.github.io</a></li>
  </ul>

  <h2>Top Skills</h2>
  <ul>
    <li>Machine Learning</li>
    <li>Time-Series</li>
    <li>Data Science</li>
    <li>Python</li>
    <li>Artificial Intelligence (AI)</li>
  </ul>

  <h2>Summary</h2>
  <p>As a Research Engineer at AIMdyn, Inc., I lead our efforts on DARPA’s SCEPTER program in collaboration with BAE Systems’ KHAOSRAZOR program, serving as the Principal Investigator for AIMdyn. In my role as Senior Technical Personnel, I collaborate closely with senior management on research strategy, bids, and proposal efforts. I help shape AIMdyn’s AI/ML strategy for new proposals and partnerships, with a focus on Koopman operator theory and control applications.</p>

<p>Outside of work, I’m an avid hiker, traveler, and cooking enthusiast. I’m also currently learning to fence.</p>

  <h2>Experience</h2>
  <ul>
    <li><strong>AIMdyn, Inc.</strong> - Research Engineer (October 2022 - Present)
      <ul>
        <li>Project Management: Led a cross-functional team of engineers and scientists on the DARPA SCEPTER/KHAOSRAZOR program, successfully securing a Phase 2 contract with BAE Systems.</li>
        <li>Algorithm Development: Designed and implemented advanced algorithms using AIMdyn’s Koopman operator theory, enhancing dynamic environment simulations.</li>
        <li>Machine Learning Pipeline: Developed and deployed an efficient ML pipeline for processing large datasets, improving data analysis speed and accuracy.</li>
        <li>Research and Development: Conducted research to develop innovative solutions, optimizing performance and scalability of dynamic simulations.</li>
        <li>Mentorship: Mentored junior engineers, fostering skill development and integration into Agile workflows.</li>
        <li>Client Engagement: Acted as the primary technical contact for clients, delivering updates and addressing engineering inquiries.</li>
      </ul>
    </li>
    <li><strong>Deloitte US - Data and Analytics</strong> - Data Scientist (June 2022 - October 2022)
      <ul>
        <li>Data Privacy: Contributed to data anonymization projects, implementing robust measures to enhance privacy and compliance.</li>
        <li>ETL Development: Developed and optimized ETL processes using Informatica, improving data flow and processing efficiency.</li>
        <li>Generative AI: Created generative AI models in Python for data anonymization, enhancing data handling processes.</li>
      </ul>
    </li>
    <li><strong>Cal Poly, San Luis Obispo</strong> - Graduate Research: Detection of Community Structure in Networks (September 2021 - June 2022)
      <ul>
        <li>Predictive Modeling: Developed a COVID-19 prediction model using Python and network analysis, demonstrating superior accuracy compared to traditional methods.</li>
        <li>Communication: Presented research findings to academic committees and the public, receiving accolades for presentation quality.</li>
      </ul>
    </li>
    <li><strong>University of California, Los Angeles</strong> - Research Intern: Modeling Deforestation in the Amazon (May 2019 - September 2019)
      <ul>
        <li>Model Design: Developed a predictive model achieving 86% accuracy in deforestation pattern analysis using time-series data.</li>
        <li>Data Analysis: Utilized MATLAB’s topography toolbox for detailed spatial data analysis, enhancing research insights.</li>
      </ul>
    </li>
  </ul>

  <h2>Education</h2>
  <ul>
    <li><strong>California Polytechnic State University-San Luis Obispo</strong> - Master of Science (MS), Applied Mathematics (June 2022)
      <ul>
        <li>Cumulative GPA: 3.8 / 4.0</li>
      </ul>
    </li>
    <li><strong>Sonoma State University</strong> - Bachelor of Arts (BA), Mathematics and Physics (May 2020)
      <ul>
        <li>Major GPA: 3.8 / 4.0</li>
        <li>Cumulative GPA: 3.65 / 4.0</li>
      </ul>
    </li>
    <li><strong>Allan Hancock College</strong> - Associate of Arts (AA), Computer Science (September 2017)</li>
  </ul>

  <h2>Skills</h2>
  <ul>
    <li>Languages: Python, SQL, MATLAB, LaTeX</li>
    <li>Tools: Git, Docker, Jira, Confluence</li>
    <li>Frameworks: Flask, pandas, numpy, scikit-learn, TensorFlow, PyTorch, Matplotlib, Seaborn</li>
    <li>Methodologies: Agile, TDD, CI/CD</li>
    <li>Research Skills: Data Analysis, Algorithm Development, ML Pipeline, Predictive Modeling, Data Anonymization, ETL</li>
    <li>Professional Skills: Project Management, Mentorship, Client Engagement, Generative AI</li>
  </ul>
</div>

<p class="end-text">Stay tuned for more updates!</p>