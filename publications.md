---
layout: default
title: Publications
---

## Publications <small>* equal contribution</small>


{% for publist in site.data.publications %}
### {{ publist.title }}
<ol class="pub {{ publist.classname }}">
{% for pub in publist.publications %}
    <li>
        {% if pub.post %}
            <a href="{{ pub.post }}">{{ pub.title }}</a>
        {% else %}
            {{ pub.title }}
        {% endif %}
        <br>
        {% for author in pub.authors %}
            {% if forloop.length == 1 %}
                {% if author contains "I. Jang" or author contains "Inkyu Jang" %}
                    <b><ins>{{ author }}</ins></b>
                {% else %}
                    {{ author }}
                {% endif %}
            {% else %}
                {% if forloop.last %}
                    {% if author contains "I. Jang" or author contains "Inkyu Jang" %}
                        and <b><ins>{{ author }}</ins></b>
                    {% else %}
                        and {{ author }}
                    {% endif %}
                {% else %}
                    {% if author contains "I. Jang" or author contains "Inkyu Jang" %}
                        <b><ins>{{ author }}</ins></b>,
                    {% else %}
                        {{ author }},
                    {% endif %}
                {% endif %}
            {% endif %}
        {% endfor %}
        {% if pub.info %}
            <br><i>{{ pub.info }}</i>
        {% endif %}
        {% if pub.conference %}
            <br><i>{{ pub.conference.name }}
            {% if pub.conference.abrv %}
                (<b>{{ pub.conference.abrv }}</b>)
            {% endif %}
            </i>
            {% if pub.conference.remark %}
                ({{ pub.conference.remark }})
            {% endif %}
        {% endif %}
        {% if pub.journal %}
            {% if pub.journal.abrv %}
                <br><i>{{ pub.journal.name }} (<b>{{ pub.journal.abrv }}</b>)</i>,
            {% else %}
                <br><i>{{ pub.journal.name }}</i>,
            {% endif %}
            {% if pub.journal.vol %}
                vol. {{ pub.journal.vol }},
            {% endif %}
            {% if pub.journal.issue %}
                no. {{ pub.journal.issue }},
            {% endif %}
            {% if pub.journal.pages %}
                pp. {{ pub.journal.pages }},
            {% endif %}
            {% if pub.journal.date %}
                {{ pub.journal.date }}.
            {% endif %}
            {% if pub.journal.remark %}
                ({{ pub.journal.remark }})
            {% endif %}
        {% endif %}
        {% if pub.award %}
            <br><b>{{ pub.award }}</b>
        {% endif %}
        {% if pub.links %}
            <br>
            {% for link in pub.links %}
                <a href="{{ link.link }}">{{ link.name }}</a>{% unless forloop.last %} | {% endunless %}
            {% endfor %}
        {% endif %}
    </li>
{% endfor %}
</ol>
{% endfor %}
