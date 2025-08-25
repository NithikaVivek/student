---
layout: default
title: Sprint 1 Home
permalink: /sprint/1/
---

<style>
body {
  background: linear-gradient(135deg, #181818 0%, #232946 100%);
  color: #f3f3f3;
  font-family: 'Segoe UI', 'Roboto', Arial, sans-serif;
  min-height: 100vh;
}
nav {
  background: #232946;
  color: #fff;
  padding: 1.2em 2em;
  display: flex;
  gap: 2em;
  align-items: center;
  border-radius: 0 0 16px 16px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.15);
}
nav a {
  color: #eebbc3;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s;
}
nav a:hover {
  color: #ffd803;
}
nav img {
  margin-right: 1em;
}
.hero {
  text-align: center;
  margin-top: 4em;
}
.hero h1 {
  font-size: 3em;
  margin-bottom: 0.3em;
  color: #ffd803;
  letter-spacing: 2px;
}
.hero p {
  font-size: 1.3em;
  color: #eebbc3;
  max-width: 600px;
  margin: 1em auto 2em auto;
}
.hero img {
  margin-top: 2em;
  border-radius: 16px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.25);
}
.card-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2em;
  margin-top: 3em;
}
.card {
  background: #232946;
  border-radius: 12px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.18);
  padding: 2em 1.5em;
  min-width: 220px;
  max-width: 260px;
  color: #f3f3f3;
  text-align: left;
  transition: transform 0.2s;
}
.card:hover {
  transform: translateY(-6px) scale(1.03);
  box-shadow: 0 8px 32px rgba(0,0,0,0.22);
}
.card-title {
  font-size: 1.2em;
  color: #ffd803;
  margin-bottom: 0.5em;
}
.card-desc {
  font-size: 1em;
  color: #eebbc3;
}
</style>

<nav>
  <img src="{{site.baseurl}}/images/logo.png" height="40" alt="Logo">
  <a href="{{site.baseurl}}/">Home</a>
  <a href="{{site.baseurl}}/sprint/1/tools">Tools & Equipment</a>
  <a href="{{site.baseurl}}/sprint/1/learning">Learning Through Mistakes</a>
  <a href="{{site.baseurl}}/sprint/1/portfolio">Portfolio & Blogging</a>
  <a href="{{site.baseurl}}/sprint/1/AI">AI Evidence</a>
  <a href="{{site.baseurl}}/sprint/1/manifesto">Manifesto</a>
  <a href="{{site.baseurl}}/sprint/1/theme">Theme & Style</a>
  <a href="{{site.baseurl}}/sprint/1/JS">JavaScript Basics</a>
  <a href="{{site.baseurl}}/tools/nithika_blog">Nithika's Blog</a>
</nav>

<div class="hero">
  <h1>Welcome to Sprint 1</h1>
  <p>Explore all my Sprint 1 work, including tools setup, agile workflow, portfolio, design, JavaScript, and more. Use the navigation bar above to jump to each section and see my progress!</p>
  <img src="{{site.baseurl}}/images/logo.png" height="100" alt="Sprint 1 Logo">
</div>

<div class="card-row">
  <div class="card">
    <div class="card-title">Tools & Equipment</div>
    <div class="card-desc">See how I set up my coding environment and automated my workflow.</div>
    <a href="{{site.baseurl}}/sprint/1/tools">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">Learning Through Mistakes</div>
    <div class="card-desc">Discover how I learned from bugs and improved my debugging skills.</div>
    <a href="{{site.baseurl}}/sprint/1/learning">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">Portfolio & Blogging</div>
    <div class="card-desc">Read my blog posts and see my project documentation.</div>
    <a href="{{site.baseurl}}/sprint/1/portfolio">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">AI Evidence</div>
    <div class="card-desc">Explore how I used AI tools to brainstorm and code smarter.</div>
    <a href="{{site.baseurl}}/sprint/1/AI">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">Manifesto</div>
    <div class="card-desc">See my collaborative work and peer reviews.</div>
    <a href="{{site.baseurl}}/sprint/1/manifesto">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">Theme & Style</div>
    <div class="card-desc">Check out my site design and layout improvements.</div>
    <a href="{{site.baseurl}}/sprint/1/theme">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">JavaScript Basics</div>
    <div class="card-desc">See my interactive UI and JS code samples.</div>
    <a href="{{site.baseurl}}/sprint/1/JS">View Section →</a>
  </div>
  <div class="card">
    <div class="card-title">Nithika's Blog</div>
    <div class="card-desc">My personal reflections and project highlights.</div>
    <a href="{{site.baseurl}}/tools/nithika_blog">View Section →</a>
  </div>
</div>
