{% if include.algset.title %}

#{% for i in (0..depth) %}#{% endfor %} {{ include.algset.title }}{% if include.algset.description %}
{{ include.algset.description }}
{% endif %}
|Case|Algorithm|
|---|---|{% assign d = depth | plus: 1 | at_most: 6 %}{% assign il = include.algset.imageLink | default: include.imageLink %}{% for alg in include.algset.algs %}{%- include algs.md algset=alg depth=d useBr=include.useBr imageLink=il bold=include.bold -%}{% endfor %}
{% elsif include.algset.first %}
{% assign encoded = include.algset[0] | url_encode | replace: "'", "%2527" %}|![Case]({{ include.imageLink | replace: "$ALG", encoded }})|{% if include.bold %}**{% endif %}{{ include.algset[0] }}{% if include.bold %}**{% endif %}{% if include.useBr %}{% assign size = include.algset | size %}{{ include.algset | slice: 1, size | join: "<br>" | prepend: "<br>"}}|{% else %}{% for a in include.algset offset:1 %}
||{{ a }}|{% endfor %}{% endif %}{% else %}
{% assign encoded = include.algset | url_encode | replace: "'", "%2527" %}|![Case]({{ include.imageLink | replace: "$ALG", encoded }})|{% if include.bold %}**{% endif %}{{ include.algset }}{% if include.bold %}**{% endif %}|{% endif %}