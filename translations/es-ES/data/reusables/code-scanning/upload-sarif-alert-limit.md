{% note %}

**Nota:** La carga de SARIF es compatible con un máximo de {% ifversion ghae-next or fpt or ghes > 3.0 %}5000{% else %}1000{% endif %} resultados por carga. Cualquier resultado que sobrepase este límite se ignorará. Si una herramienta genera demasiados resultados, debes actualizar la configuración para enfocarte en los resultados de las reglas o consultas más importantes.

{% endnote %}
