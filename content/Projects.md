---
title: Projects
draft: false
tags: []
---
## Background

Below is a high level overview of external projects and academic endeavours I have pursued outside of the current employment. Linked to each project is a detailed set of notes should anyone want to follow a similar path and try these projects for themselves.


---


## Optimal Area Modelling

![[optimal_areas.jpeg|500x300]]


### Summary
The objective of this project is to model and identify optimal living areas in Cape Town by considering both work location and various quality-of-life factors derived from census data.

Users can input their work location, which is then processed using the Google Maps API to calculate commute times to and from each suburb in Cape Town. This commuting data is integrated with a comprehensive dataset evaluating the quality of life across different postal codes, utilizing information gathered from government websites and South African Census data.

The findings are presented through a geospatial visualization created in Power BI, enabling users to easily identify the most suitable areas to live based on their individual needs and preferences.

This project draws inspiration from the work of [Lloyd Richards](https://www.linkedin.com/posts/lloydrichards_moving-house-like-an-actuary-collect-data-activity-7188109495196135424-g52l?utm_source=share&utm_medium=member_desktop), who effectively illustrated the application of data modeling in the context of real estate decisions.

### Technologies Used
- Python
- Google Maps API
- Pandas
- Power BI Geospatial visualisation
- Beautiful Soup Web Scraping

### Detailed Notes

[[Projects Folder/Optimal Area/Optimal Area - Project Outline]]

---

## Introduction to Machine Learning


![[machine_diagram.png|500x300]]

### Summary

This project marked my journey from having no prior experience to completing my first-ever machine learning project. Inspired by the article _[End-to-End Machine Learning Project: Churn Prediction](https://medium.com/@ramazanolmeez/end-to-end-machine-learning-project-churn-prediction-e9c4d0322ac9)_ by Ramazan Olmez, I set an end goal of performing churn analysis on a publicly available telecommunications dataset. I then worked backward to identify the various aspects of statistics and coding I needed to learn along the way.

To organize my learning, I created a flow diagram outlining each key concept and skill. I documented my notes for every stage, covering the foundations of machine learning, statistics, and coding. These notes were designed not only to guide my own learning but also to help others eager to move beyond the hype and actually build their first machine learning project.

Throughout my journey, I found valuable resources, including Josh Starmer's _Stats Quest_ videos on YouTube, which clarified many complex topics, and the article _[Gradient Boosting Algorithm: A Complete Guide for Beginners](https://www.analyticsvidhya.com/blog/2021/09/gradient-boosting-algorithm-a-complete-guide-for-beginners/)_ by Anshul Saini, which provided essential insights into one of the key algorithms I explored.

While the primary goal was to complete the churn analysis, this project also serves as a practical resource for anyone looking to get started in machine learning.


### Technologies Used
- Python
- Scikit-Learn
- Pandas

### Final Project

[[Projects Folder/Machine Learning/Final Project]]


### Detailed Notes

1. [[Projects Folder/Machine Learning/Classification Trees]]
2. [[Projects Folder/Machine Learning/Decision Trees]]
3. [[Projects Folder/Machine Learning/Bias vs Variance]]
4. [[Projects Folder/Machine Learning/Encoding]]
5. [[Projects Folder/Machine Learning/Random Forest]]
6. [[Projects Folder/Machine Learning/AdaBoost]]
7. [[Projects Folder/Machine Learning/Gradient Boost]]
8. [[Cosine Similarity]]
9. [[CatBoost]]

---

## Volunteer Web Development

![[Pasted image 20241106190431.png]]

### Summary

While volunteering with ObsCanFeedYou, I noticed a gap in tracking the impact we were making each weekend. Seeing an opportunity, I set out to create a custom website to help the team record and visualize the number of people fed weekly.

Starting from scratch, I taught myself web development, covering both front-end and back-end skills. I built a database to store feeding data and developed a user-friendly interface to display weekly stats. To make data input easier for volunteers, I integrated WhatsApp using an API, allowing them to send a simple message to update the database.

This project gave me hands-on experience in full-stack development, database management, and real-time communication—tools that help ObsCanFeedYou keep track of its impact in the community effortlessly.

### Technologies Used

- **Languages**: TypeScript, JavaScript, Python, SQL
- **Frontend**: React, Tailwind CSS
- **Backend**: Next.js, Flask
- **Database**: Supabase
- **ORM**: Prisma
- **Communication/API**: Vonage API for WhatsApp integration
- **Hosting/Deployment**: Render, Vercel


### Detailed Notes

[[ObsCan Website - Project Outline]]