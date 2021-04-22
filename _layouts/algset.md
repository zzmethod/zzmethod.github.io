---
layout: page
---
{% capture newLine %}
{% endcapture %}
{% capture content %}{%- if page.description -%}{{ page.description }}{%- endif -%}{% assign bold = page.bold | default: true %}
{% for alg in page.algs %}{%- include algs.md algset=alg depth=2 useBr=true imageLink=page.imageLink bold=bold -%}
{% endfor %}{% if end %}
{{ end }}{{ newLine }}{% endif %}{% if page.footer or page.author %}
---

{% if page.footer %}{{ page.footer }}  {% endif %}
{% if page.author %}By {{ page.author }}{% endif %}{% endif %}{% endcapture %}{{ content | markdownify | replace: "’", "'" }}