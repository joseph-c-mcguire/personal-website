---
layout: page
title: Home
---

<style>
  .header-image {
    border-radius: 50%;
    width: 150px;
    height: 150px;
    object-fit: cover;
    display: block;
    margin: 0 auto;
  }
  .welcome-text {
    text-align: center;
    font-family: 'Arial', sans-serif;
    color: #333;
  }
  .latest-posts {
    font-family: 'Arial', sans-serif;
    color: #555;
  }
  .resume-section {
    font-family: 'Arial', sans-serif;
    color: #333;
    margin: 20px 0;
  }
  .resume-section h2 {
    color: #555;
  }
  .resume-section ul {
    list-style-type: none;
    padding: 0;
  }
  .resume-section ul li {
    margin: 5px 0;
  }
</style>

<div class="welcome-text">
  <h1>Joseph McGuire</h1>
  <img src="images/headshot.jpg" alt="Joseph McGuire" class="header-image">
  <p>Thank you for visiting my blog. Here, you'll find a collection of my thoughts, experiences, and insights on various topics. Whether you're here to learn something new, get inspired, or just pass the time, I hope you find something that resonates with you.</p>
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
    <li>Email: <a href="mailto:joseph.c.mcg@gmail.com">joseph.c.mcg@gmail.com</a></li>
    <li>LinkedIn: <a href="https://www.linkedin.com/in/joseph-c-mcg">www.linkedin.com/in/joseph-c-mcg</a></li>
  </ul>

  <h2>Top Skills</h2>
  <ul>
    <li>Machine Learning</li>
    <li>Time-Series</li>
    <li>Data Science</li>
    <li>Python</li>
    <li>Artificial Intelligence (AI)</li>
    <li>Multi-Agent Control Theory</li>
  </ul>

  <h2>Summary</h2>
  <p>As a Research Engineer at AIMdyn, Inc., I lead our efforts on DARPA’s SCEPTER program in collaboration with BAE Systems’ KHAOSRAZOR program, serving as the Principal Investigator for AIMdyn. In my role as Senior Technical Personnel, I collaborate closely with senior management on research strategy, bids, and proposal efforts. I help shape AIMdyn’s AI/ML strategy for new proposals and partnerships, with a focus on Koopman operator theory and control applications.<\p>

<p>My interests lie in climate science, digital twin creation, surrogate modeling frameworks, and design space optimization. I’m always eager to connect with scientists and engineers working on AI/ML-related projects. Feel free to reach out if you’d like to chat!
</p>

<p>Outside of work, I’m an avid hiker, traveler, and cooking enthusiast. I’m also currently learning to fence.</p>

  <h2>Experience</h2>
  <ul>
    <li><strong>AIMdyn, Inc.</strong> - Research Engineer (October 2022 - Present)</li>
    <li><strong>Deloitte</strong> - Data Scientist (June 2022 - October 2022)</li>
    <li><strong>UAW Local 4123</strong> - Financial Secretary (March 2021 - May 2022)</li>
    <li><strong>California Polytechnic State University (Cal Poly)</strong> - Teaching Assistant (September 2020 - May 2022)</li>
    <li><strong>Sonoma State University</strong> - Mathematics Grader (January 2019 - May 2020)</li>
    <li><strong>Sonoma State University</strong> - Student Researcher (May 2018 - May 2020)</li>
    <li><strong>University of California, Los Angeles</strong> - Undergraduate Researcher (May 2019 - September 2019)</li>
  </ul>

  <h2>Education</h2>
  <ul>
    <li><strong>California Polytechnic State University-San Luis Obispo</strong> - Master of Science (MS), Applied Mathematics (September 2020 - June 2022)</li>
    <li><strong>Sonoma State University</strong> - Bachelor of Arts (BA), Mathematics (2017 - 2020)</li>
    <li><strong>Sonoma State University</strong> - Bachelor of Arts (BA), Physics (2017 - 2020)</li>
    <li><strong>Allan Hancock College</strong> - Associate of Arts (AA), Computer Science (2013 - 2017)</li>
  </ul>

<p class="welcome-text">Stay tuned for more updates!</p>