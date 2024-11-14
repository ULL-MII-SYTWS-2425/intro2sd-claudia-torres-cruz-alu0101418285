---
title: "Películas de Terror para ver en Halloween 2024"
excerpt: "Recomendaciones sobre las películas que más impacto están teniendo este 2024 para hacer maratón"
---
<head>
  <style>
    .pelicula {
      display: flex;
      align-items: flex-start;
      gap: 20px;
      margin-bottom: 30px;
    }
    .poster{
      width: 180px;
      height: auto;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
    }
    .pelicula-details {
      max-width: 600px;
    }
    .pelicula-title {
      font-size: 1.8em;
      color: #333;
      margin: 0;
    }
    .pelicula-info p {
      font-size: 1.1em;
      color: #555;
      margin: 5px 0;
    }
    .pelicula-description {
      font-size: 0.8rem !important;
      color: #666;
      margin-top: 10px;
    }
    .plataformas {
      display: flex;
      gap: 15px;
      margin-top: 30px;
    }
    .platform-logo {
      width: auto;
      height: 40px;
      transition: transform 0.3s;
    }
    .platform-logo:hover {
      transform: scale(1.1);
    }
    hr {
      border: 1px solid #ccc;
      margin-top: 20px;
    }
  </style>
</head>

Halloween está a la vuelta de la esquina, y qué mejor manera de celebrar la noche más espeluznante del año que con un maratón de películas de terror. Aquí tienes una selección de las películas más aterradoras que puedes ver este 31 de octubre, junto con las plataformas en las que están disponibles.

{% for pelicula in site.data.best-horror-films %}
<div class="pelicula">
  <img class="poster" src="{{ pelicula.Poster }}" alt="Poster de {{ pelicula.Title }}">
  <div class="pelicula-details">
    <h3 class="pelicula-title">{{ pelicula.Title }}</h3>
    <div class="pelicula-info">
      <p><strong>Año:</strong> {{ pelicula.Year }}</p>
      <p><strong>Género:</strong> {{ pelicula.Genre }}</p>
      <p><strong>Duración:</strong> {{ pelicula.Duration }} minutos</p>
    </div>
    <div class="plataformas">
      {% if pelicula['Prime Video'] == 'true' %}
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Amazon_Prime_Video_logo_%282022%29.svg/640px-Amazon_Prime_Video_logo_%282022%29.svg.png" alt="Prime Video" class="platform-logo">
      {% endif %}

      {% if pelicula['Disney Plus'] == 'true' %}
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Disney%2B_logo.svg/800px-Disney%2B_logo.svg.png?20240603202835" alt="Disney Plus" class="platform-logo">
      {% endif %}

      {% if pelicula['HBO Max'] == 'true' %}
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/HBO_logo.svg/640px-HBO_logo.svg.png" alt="HBO Max" class="platform-logo">
      {% endif %}

      {% if pelicula['Netflix'] == 'true' %}
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Netflix_Logomark.png/640px-Netflix_Logomark.png" alt="Netflix" class="platform-logo">
      {% endif %}
    </div>
  </div>
</div>
<p class="pelicula-description"><strong>Descripción: </strong>{{ pelicula.Description }}</p>
<hr>
{% endfor %}
