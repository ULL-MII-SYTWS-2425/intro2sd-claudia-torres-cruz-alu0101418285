---
title: "Películas de Terror para ver en Halloween 2024"
---

Halloween está a la vuelta de la esquina, y qué mejor manera de celebrar la noche más espeluznante del año que con un maratón de películas de terror. Aquí tienes una selección de las películas más aterradoras que puedes ver este 31 de octubre, junto con las plataformas en las que están disponibles.

{% for pelicula in site.data.best-horror-films %}
### **{{ pelicula.Title }}**  
**Año:** {{ pelicula.Year }}  
**Género:** {{ pelicula.Genre }}  
**Duración:** {{ pelicula.Duration }} minutos  
**Descripción:** {{ pelicula.Description }}  
**Disponible en:**  
  {% if pelicula['Prime Video'] == 'true' %}
 <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Amazon_Prime_Video_logo_%282022%29.svg/640px-Amazon_Prime_Video_logo_%282022%29.svg.png" alt="Prime Video" style="width: 120px; height: auto;">
  {% endif %}

  {% if pelicula['Disney Plus'] == 'true' %}
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Disney%2B_logo.svg/800px-Disney%2B_logo.svg.png?20240603202835" alt="Disney plus" style="width: 120px; height: auto;">
  {% endif %}

  {% if pelicula['HBO Max'] == 'true' %}
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/HBO_logo.svg/640px-HBO_logo.svg.png" alt="HBO MAX" style="width: 120px; height: auto;">
  {% endif %}
  
  {% if pelicula['Netflix'] == 'true' %}
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Netflix_Logomark.png/640px-Netflix_Logomark.png" alt="NETFLIX" style="width: 120px; height: auto;">
  {% endif %}
{% endfor %}
