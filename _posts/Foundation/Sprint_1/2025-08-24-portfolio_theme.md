---
layout: post
title: Portfolio Theme
description: Portfolio Theme
permalink: /sprint/1/portfolio-theme
breadcrumb: true
toc: true
nav: sprint_1.html
---

# Reflecting on My Rock-Paper-Scissors Console Game
This week, I focused on refining a simple Rock-Paper-Scissors game in Python. What began as a casual coding experiment turned into a meaningful exercise in user experience, iteration, and learning design. It showed me that even small projects can reveal bigger lessons about problem-solving, patience, and thoughtful design.

## Portfolio & Blogging
Challenges and Solutions
My initial goal was straightforward: build a working game that lets players choose moves and see if they win against the computer. But the first real challenge came quickly — handling invalid inputs.

Another hurdle was keeping the game engaging. Playing one round felt flat and directionless. Introducing a score system and feedback after each round changed that completely. Those simple additions created a sense of progress and motivation, making each round more rewarding.

Lesson Learned: Programs should guide users with care — we can’t assume every input will be perfect.

## Growth in LxD Thinking
Working on this project helped me think more like a learning experience designer, even though it was just a console game. I reflected on how effective design helps users learn and persist:

Guiding the learner by removing barriers and maintaining engagement.

Providing immediate feedback through scores and outcomes.

Embracing iteration and improvement — each version of the game felt more polished than the last.

Insight: Learning experience design isn’t about flashy visuals — it’s about empathy and clarity from the user’s point of view.

## Theme, Style, and Layout
Even text-based programs benefit from good design. Early versions of my game dumped all text in one block, which felt confusing. Adding visual structure and contextual cues made the experience smoother and more intuitive.

Key design updates:

Section headers marked the start of each round.

Score updates kept players invested.

A quit option gave players control, reducing stress and frustration.

Reflection: Even subtle interface decisions can elevate an experience from functional to enjoyable.

Example CSS Enhancements
If I were to turn this into a website, I’d use CSS to make it more appealing and easier to navigate.

## Highlighting the Current Round

css
.current-round {
  background-color: #e0f7fa;
  border-left: 4px solid #00796b;
  padding: 10px;
  margin-bottom: 16px;
  font-weight: bold;
}
Score Display Styling

css
.score-box {
  background: #fff3e0;
  color: #e65100;
  border-radius: 8px;
  padding: 8px 16px;
  font-size: 1.2em;
  display: inline-block;
  margin: 10px 0;
  box-shadow: 0 2px 8px rgba(0,0,0,0.07);
}
Button Enhancements

css
button {
  background: linear-gradient(90deg, #6b4bd3 0%, #327fc7 100%);
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 10px 20px;
  font-size: 1em;
  cursor: pointer;
  transition: background 0.3s;
}
button:hover {
  background: linear-gradient(90deg, #327fc7 0%, #6b4bd3 100%);
}
These enhancements would highlight key actions, guide attention, and create a more engaging experience.

<img src="{{ site.baseurl }}/images/no_CSS.jpg" alt="NO_CSS"> <img src="{{ site.baseurl }}/images/CSS.jpg" alt="CSS">
Reflection and Introspection
This project became a lesson in patience, empathy, and self-awareness. Early bugs were frustrating, but each debugging session reinforced the value of small, steady progress.

I also discovered that my assumptions about users were often wrong. I expected flawless input and immediate understanding. Designing better instructions and feedback forced me to see the game through a beginner’s eyes.

Each iteration — adding scores, a quit option, clearer layout — deepened my understanding of how reflection drives improvement. It reinforced that designing for real users means constantly pausing, testing, and reevaluating.

<img src="{{ site.baseurl }}/images/DB.jpg" alt="DB">

## Next Steps
Looking ahead, I plan to:

Add a best-of-N mode for structured gameplay.

Implement a simple learning AI that adapts to player choices.

Experiment with colored text and formatting for better clarity and engagement.

In the end, this small console game taught me big lessons about empathy, iteration, and user-centered design. It reminded me that reflection — thinking through the user experience — matters just as much as writing the code itself.
