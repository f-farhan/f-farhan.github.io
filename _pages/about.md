---
title: "About"
description: "Biography, awards and academic background of Faisal Farhan"
layout: gridlay
permalink: /about/
---

## About 


{% for member in site.data.pi %}

<div class="row">
  <img src="{{ site.url }}{{ site.baseurl }}/images/team/{{ member.photo-large }}" alt="{{ member.name }}" class="img-responsive avatar-about" />
  <h3>{{ member.name }}</h3>
  <i style="font-size:20px">{{ member.info }}</i><br>

  {% if member.website %}<a href="{{ member.website }}" target="_blank"><i class="fa fa-home fa-3x"></i></a> {% endif %}
  {% if member.email %}<a href="mailto:{{ member.email }}" target="_blank"><i class="fa fa-envelope-square fa-3x"></i></a> {% endif %}
  <a href="{{ '/files/Faisal_Farhan_CV.pdf' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="View my CV (PDF)">
  <i class="ai ai-cv-square ai-3x"></i>
   </a>
  {% if member.orcid %} <a href="{{ member.orcid }}" target="_blank"><i class="ai ai-orcid-square ai-3x"></i></a> {% endif %}
  {% if member.linkedin %} <a href="{{ member.linkedin }}" target="_blank"><i class="fa fa-linkedin-square fa-3x"></i></a> {% endif %}
  {% if member.scholar %} <a href="{{ member.scholar }}" target="_blank"><i class="ai ai-google-scholar-square ai-3x"></i></a> {% endif %}
  {% if member.researchgate %} <a href="{{ member.researchgate }}" target="_blank"><i class="ai ai-researchgate-square ai-3x"></i></a> {% endif %}
  {% if member.github %} <a href="{{ member.github }}" target="_blank"><i class="fa fa-github-square fa-3x"></i></a> {% endif %}
  <ul style="overflow: hidden">

  {% if member.number_educ == 1 %}
  <li> {{ member.education1 }} </li>
  {% endif %}

  {% if member.number_educ == 2 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  {% endif %}

  {% if member.number_educ == 3 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  <li> {{ member.education3 }} </li>
  {% endif %}

  {% if member.number_educ == 4 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  <li> {{ member.education3 }} </li>
  <li> {{ member.education4 }} </li>
  {% endif %}

  {% if member.number_educ == 5 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  <li> {{ member.education3 }} </li>
  <li> {{ member.education4 }} </li>
  <li> {{ member.education5 }} </li>
  {% endif %}

  {% if member.number_educ == 6 %}
  <li> {{ member.education1 }} </li>
  <li> {{ member.education2 }} </li>
  <li> {{ member.education3 }} </li>
  <li> {{ member.education4 }} </li>
  <li> {{ member.education5 }} </li>
  <li> {{ member.education6 }} </li>
  {% endif %}

  </ul>
</div>

{% endfor %}

## Short biography

<div class="short-bio">
I am currently working as a Lecturer at Ahsanullah University of Science & Technology, Dhaka, Bangladesh. I completed my Erasmus Mundus Joint master’s Degree in Medical Imaging and Applications (MAIA) in 2025, coordinated by the University of Girona, Spain, along with the Université de Bourgogne, France and the University of Cassino and Southern Lazio, Italy as partner universities. I worked as a Graduate Research Intern at Laboratoire en Imagerie et Vision Artificielle (ImVIA) in Dijon, France where i did my thesis titled “Design and Validation of Multimodal and Lightweight Handheld ST-rPPG Acquisition Systems for Physiological measurements” under the supervision of Prof. Yannick Benezeth.

I received my Bachelor’s degree in Electrical and Electronic Engineering from Ahsanullah University of Science & Technology , Dhaka, Bangladesh. 
My current research interest includes Signal Processing, Medical Imaging, Image Processing, Machine Learning & Deep Learning.
</div>

{% if site.data.awards %}
## Awards
<div class="rowl1" style="padding-top: 10px;">

{% for award in site.data.awards %}
{{ forloop.index }}. {% if award.name_url %}<a href="{{ award.name_url }}" target="_blank">{% endif %}<strong>{{ award.name }}</strong>{% if award.name_url %}</a>{% endif %} {% if award.organisation %} from {% if award.organisation_url %}<a href="{{ award.organisation_url }}" target="_blank">{% endif %} {{ award.organisation }}{% if award.organisation_url %}</a>{% endif %}{% endif %}{% if award.subtitle %}: {{ award.subtitle }}{% endif %} ({{ award.year }}).
{% endfor %}
</div>
{% endif %}

{% comment %}
{% if site.data.grants %}
## Grants
<div class="rowl1" style="padding-top: 10px;">

{% for grant in site.data.grants %}
{{ forloop.index }}. {% if grant.name_url %}<a href="{{ grant.name_url }}" target="_blank">{% endif %}<strong>{{ grant.name }}</strong>{% if grant.name_url %}</a>{% endif %} {% if grant.organisation %} from {% if grant.organisation_url %}<a href="{{ grant.organisation_url }}" target="_blank">{% endif %} {{ grant.organisation }}{% if grant.organisation_url %}</a>{% endif %}{% endif %}{% if grant.subtitle %}: {{ grant.subtitle }}{% endif %} ({{ grant.year }}).
{% endfor %}
</div>
{% endif %}
{% endcomment %}

{% if site.data.collaborators %}
## Collaborations
<div class="rowl1" style="padding-top: 10px;">

{% for collaborator in site.data.collaborators %}
{{ forloop.index }}. {% if collaborator.name_url %}<a href="{{ collaborator.name_url }}" target="_blank">{% endif %}<strong>{{ collaborator.name }}</strong>{% if collaborator.name_url %}</a>{% endif %} ({{ collaborator.field }}, {% if collaborator.institution_url %}<a href="{{ collaborator.institution_url }}" target="_blank">{% endif %}{{ collaborator.institution }}{% if collaborator.institution_url %}</a>{% endif %}).
{% endfor %}
</div>
{% endif %}

{% comment %}
{% if site.data.research_visits %}
## Research visits
<div class="rowl1" style="padding-top: 10px;">

{% for research_visit in site.data.research_visits %}
{{ forloop.index }}. {% if research_visit.institution_url %}<a href="{{ research_visit.institution_url }}" target="_blank">{% endif %}<strong>{{ research_visit.institution }}</strong>{% if research_visit.institution_url %}</a>{% endif %}{% if research_visit.location %} ({{ research_visit.location }}){% endif %}{% if research_visit.period %}, {{ research_visit.period }}{% endif %}.
{% endfor %}
</div>
{% endif %}
{% endcomment %}

{% comment %}
{% if site.data.invited_speakers %}
## Invited speakers at my group
<div class="rowl1" style="padding-top: 10px;">

{% for invited_speaker in site.data.invited_speakers %}
{{ forloop.index }}. {% if invited_speaker.name_url %}<a href="{{ invited_speaker.name_url }}" target="_blank">{% endif %}<strong>{{ invited_speaker.name }}</strong>{% if invited_speaker.name_url %}</a>{% endif %} ({{ invited_speaker.field }}, {% if invited_speaker.institution_url %}<a href="{{ invited_speaker.institution_url }}" target="_blank">{% endif %}{{ invited_speaker.institution }}{% if invited_speaker.institution_url %}</a>{% endif %}){% if invited_speaker.venue %} – at {{ invited_speaker.venue }}{% endif %}{% if invited_speaker.date %}, {{ invited_speaker.date }}{% endif %}.
{% endfor %}
</div>
{% endif %}
{% endcomment %}
