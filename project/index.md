---
layout: default
permalink: /project/
---

<div class="week hrow">
    <div class="week_id">Week</div>
    <div class="date">Deadline (5pm)</div>
    <div class="topic">Team</div>
    <div class="topic">Individual</div>
	<div class="topic">Rubric</div>
</div>

{% assign week_id = 0 %}
{% for e in site.data.project %}
<div class="week {% cycle "odd", "even" %}">
    {% if e.break %}
    <div class="week_id"></div>
    <div class="date"></div>
	<div class="topic">{{e.break}}</div>
    {% else %}
    {% assign week_id = week_id | plus: 1 %}
    <div class="week_id">{{week_id}}</div>
    <div class="date"></div>
    {% if e.type == 'individual' %}
         <div class="topic"></div>
    {% endif %}
    {% if e.handout %}
    <div class="topic"><a href="{{e.handout}}">{{e.week}}</a></div>
    {% else %}
    <div class="topic">{{e.week}}</div>
    {% endif %}
    {% if e.type == 'team' %}
         <div class="topic"></div>
    {% endif %}
    {% if e.rubric %}
    <div class="topic">
        <ul>
            {% for r in e.rubric %}
                {% for pair in r %}
                    {% if pair[1] == nil %}
                        <li>{{r}}</li>
                    {% else %}
                        <li><a href="{{pair[1]}}">{{pair[0]}}</a></li>
                    {% endif %}
                {% endfor %}
            {% endfor %}
        </ul>
    </div>
    {% endif %}
    {% endif %}
</div>
{% endfor %}

<script type="text/javascript">
   make_schedule({{site.data.settings.first}},7,0);
</script>
   

