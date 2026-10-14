---
title: "Teaching"
description: "Teaching and student supervision by Faisal Farhan."
layout: gridlay
permalink: /education/
status: false
---

# Teaching and Supervision

{% if site.courses.size > 0 %}
{% assign courses = site.courses | sort: 'year_start' | reverse %}

## Courses
<div class="rowl1" style="padding-top: 10px;">

{% for course in courses %}
{{ forloop.index }}. {% if course.url %}<a href="{{ course.url | relative_url }}">{% endif %}<strong>{{ course.name }}</strong>{% if course.url %}</a>{% endif %} ({{ course.institution }}, {{ course.year_start }}–{{ course.year_end }}) {% if course.type == 'bsc' %}<button class="btn-completed">BSc</button>{% endif %}{% if course.type == 'msc' %}<button class="btn-inprogress">MSc</button>{% endif %}{% if course.type == 'phd' %}<button class="btn-notstarted">PhD</button>{% endif %}{% if course.comment %} – {{ course.comment }}{% endif %}
<br/>
<i>{{ course.code }}. {{ course.subheading }}</i>.

{% endfor %}

</div>
{% endif %}


{% comment %}
Temporarily hidden: Guest lectures.

{% if site.data.lectures.size > 0 %}
{% assign lectures = site.data.lectures | sort: 'year' | reverse %}

## Guest lectures
<div class="rowl1" style="padding-top: 10px;">

{% for lecture in lectures %}
{{ forloop.index }}. {{ lecture.name }} ({{ lecture.year }}).
{% endfor %}

</div>
{% endif %}
{% endcomment %}


{% comment %}
Temporarily hidden: Supervision of PhD students.

{% if site.data.supervision_phd.size > 0 %}
{% assign students = site.data.supervision_phd | sort: 'year' | reverse %}

## Supervision of PhD students
<div class="rowl1" style="padding-top: 10px;">

{% for student in students %}
{{ forloop.index }}. {% if student.name_url %}<a href="{{ student.name_url }}" target="_blank" rel="noopener noreferrer">{% endif %}<strong>{{ student.name }}</strong>{% if student.name_url %}</a>{% endif %} ({{ student.year }}){% if student.comment %} – {{ student.comment }}{% endif %}
<br/>
<i>{{ student.project }}</i>{% if student.project_url %} (<a href="{{ student.project_url }}" target="_blank" rel="noopener noreferrer">link</a>){% endif %}.

{% endfor %}

</div>
{% endif %}
{% endcomment %}


{% comment %}
Temporarily hidden: Supervision of MSc students and student groups.

{% if site.data.supervision_msc.size > 0 %}
{% assign students = site.data.supervision_msc | sort: 'year' | reverse %}

## Supervision of MSc students and student groups
<div class="rowl1" style="padding-top: 10px;">

{% for student in students %}
  {% assign pdffile = false %}
  {% if student.project_url %}
    {% if student.project_url contains '/' %}
      {% assign pdffile = student.project_url %}
    {% else %}
      {% assign pdffile = "/p/students/" | append: student.project_url | append: ".pdf" | relative_url %}
    {% endif %}
  {% endif %}

{{ forloop.index }}. {% if student.name_url %}<a href="{{ student.name_url }}" target="_blank" rel="noopener noreferrer">{% endif %}<strong>{{ student.name }}</strong>{% if student.name_url %}</a>{% endif %} ({{ student.year }}){% if student.comment %} – {{ student.comment }}{% endif %}
<br/>
<i>{{ student.project }}</i>{% if pdffile %} (<a href="{{ pdffile }}" target="_blank" rel="noopener noreferrer">link</a>){% endif %}.

{% endfor %}

</div>
{% endif %}
{% endcomment %}


{% if site.data.supervision_bsc.size > 0 %}
{% assign students = site.data.supervision_bsc | sort: 'year' | reverse %}

## Supervision of BSc students and student groups
<div class="rowl1" style="padding-top: 10px;">

{% for student in students %}
  {% assign pdffile = false %}
  {% if student.project_url %}
    {% if student.project_url contains '/' %}
      {% assign pdffile = student.project_url %}
    {% else %}
      {% assign pdffile = "/p/students/" | append: student.project_url | append: ".pdf" | relative_url %}
    {% endif %}
  {% endif %}

{{ forloop.index }}. {% if student.name_url %}<a href="{{ student.name_url }}" target="_blank" rel="noopener noreferrer">{% endif %}<strong>{{ student.name }}</strong>{% if student.name_url %}</a>{% endif %} ({{ student.year }}){% if student.comment %} – {{ student.comment }}{% endif %}
<br/>
<i>{{ student.project }}</i>{% if pdffile %} (<a href="{{ pdffile }}" target="_blank" rel="noopener noreferrer">link</a>){% endif %}.

{% endfor %}

</div>
{% endif %}


{% if site.data.supervision_internship.size > 0 %}
{% assign students = site.data.supervision_internship | sort: 'year' | reverse %}

## Supervision of Projects
<div class="rowl1" style="padding-top: 10px;">

{% for student in students %}
  {% assign pdffile = false %}
  {% if student.project_url %}
    {% if student.project_url contains '/' %}
      {% assign pdffile = student.project_url %}
    {% else %}
      {% assign pdffile = "/p/students/" | append: student.project_url | append: ".pdf" | relative_url %}
    {% endif %}
  {% endif %}

{{ forloop.index }}. {% if student.name_url %}<a href="{{ student.name_url }}" target="_blank" rel="noopener noreferrer">{% endif %}<strong>{{ student.name }}</strong>{% if student.name_url %}</a>{% endif %} ({{ student.year }}){% if student.comment %} – {{ student.comment }}{% endif %}
<br/>
<i>{{ student.project }}</i>{% if pdffile %} (<a href="{{ pdffile }}" target="_blank" rel="noopener noreferrer">link</a>){% endif %}.

{% endfor %}

</div>
{% endif %}


{% comment %}
Temporarily hidden: Defence committees.

{% if site.data.supervision_defence.size > 0 %}
{% assign students = site.data.supervision_defence | sort: 'year' | reverse %}

## Defence committees
<div class="rowl1" style="padding-top: 10px;">

{% for student in students %}
  {% assign pdffile = false %}
  {% if student.project_url %}
    {% if student.project_url contains '/' %}
      {% assign pdffile = student.project_url %}
    {% else %}
      {% assign pdffile = "/p/students/" | append: student.project_url | append: ".pdf" | relative_url %}
    {% endif %}
  {% endif %}

{{ forloop.index }}. {% if student.name_url %}<a href="{{ student.name_url }}" target="_blank" rel="noopener noreferrer">{% endif %}<strong>{{ student.name }}</strong>{% if student.name_url %}</a>{% endif %} ({% if student.degree %}{{ student.degree }}, {% endif %}{{ student.year }}){% if student.institution %} – at {{ student.institution }}{% endif %}{% if student.status == 'fail' %} <button class="btn-notstarted">FAIL</button>{% endif %}
<br/>
<i>{{ student.project }}</i>{% if pdffile %} (<a href="{{ pdffile }}" target="_blank" rel="noopener noreferrer">link</a>){% endif %}.

{% endfor %}

</div>
{% endif %}
{% endcomment %}