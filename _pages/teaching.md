---
layout: page
permalink: /teaching/
title: learning
description: This section is to keep track of all the courses that I'll be taking from now on. I've found specially useful to write about some new topic that a I'm learning and sometimes 'not learning'  or not totally getting the concept.  

---

<!---
For now, this page is assumed to be a static description of your courses. You can convert it to a collection similar to `_projects/` so that you can have a dedicated page for each course.

Organize your courses by years, topics, or universities, however you like!
--->

The format is pretty standard for all the courses, or at least what I've found to be most effective for me, a course divided in 18 weeks with a dedication of 15 hours/week
- Schedule:
	- [week1]
	- [week2]

	...
	- Week18


- Labs: Usually 1 per week of 2 hour long to program the concepts. They are not gonna be specially hard. Hopefully all will be kind of guided homeworks to get a better understanding of the weekly conccepts. 

- Homeworks: 1 per month. An aplied problem that puts together all 

- Final Project: 1 per course. It's very possible that I mix it with 

{% for project in site.project %}

{% if project.redirect %}
<div class="project">
    <div class="thumbnail">
        <a href="{{ project.redirect }}" target="_blank">
        {% if project.img %}
        <img class="thumbnail" src="{{ project.img | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <h1>{{ project.title }}</h1>
            <br/>
            <p>{{ project.description }}</p>
        </span>
        </a>
    </div>
</div>
{% else %}

<div class="project ">
    <div class="thumbnail">
        <a href="{{ project.url | prepend: site.baseurl | prepend: site.url }}">
        {% if project.img %}
        <img class="thumbnail" src="{{ project.img | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <h1>{{ project.title }}</h1>
            <br/>
            <p>{{ project.description }}</p>
        </span>
        </a>
    </div>
</div>

{% endif %}

{% endfor %}