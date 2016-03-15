<div markdown='1' class='alert alert-{{ include.type }}'>
{% if include.type == 'warning' %}
  **Important note**
{% else %}
  **Note**
{% endif %}
{{ include.message }}
</div>
