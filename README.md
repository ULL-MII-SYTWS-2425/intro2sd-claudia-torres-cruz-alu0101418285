# Informe - Práctica Introduction to system development 


## Resumen del primer capítulo del libro
El resumen del primer capítulo del libro se encuentra en el apartado posts, el día 01/10/2022. En este apartado se ha usado Liquid para iterar sobre las etapas tecnológicas y para que al final del post aparezca como autora:

El front matter del archivo contiene:

```yml
author: "Claudia Torres Cruz"
stages:
  - Viabilidad del estudio
  - Requisitos de ingeniería
  - Diseño del sistema
  - Desarrollo del software
  - Implementación de la solución
```

Se utiliza Liquid para iterar sobre los elementos, colocarlos en una lista ordenada y añadir información extra en uno de los casos:

```md
{% for stage in page.stages %}
  {% if stage == "Requisitos de ingeniería" %}
1. **{{ stage }}** para analizar las necesidades tanto de la empresa como de los usuarios
  {% else %}
1. **{{ stage }}**
  {% endif %}
{% endfor %}
```

También, para añadirme como autora al final de la página:

```md
Escrito por: {{ page.author }}
```

## Reconfiguración del archivo _config.yml

Se han ajustado los valores del archivo `_config.yml` para modificar:
- El nombre, el avatar y las URLs de contacto.

```yml
author:
  name             : *name 
  avatar           : "/assets/images/imagen_perfil.png"
  bio              : "Estudiante del máster en Ingeniería Informática ULL"
  location         : "Tenerife, Islas Canarias"
  links:
    - label: "Linkedin"
      icon: "fab fa-fw fa-linkedin"
      url: "https://www.linkedin.com/in/claudia-torres-cruz-6ab379267/"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      url: "https://twitter.com/Claudia_TC2002"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/ClaudiaTC02"
```

- El footer y algunos iconos.

```yml
footer:
  links:
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      url: "https://twitter.com/Claudia_TC2002"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/ClaudiaTC02"
    - label: "Linkedin"
      icon: "fab fa-fw fa-linkedin"
      url: "https://www.linkedin.com/in/claudia-torres-cruz-6ab379267/"
```

```yml
logo                     : "/assets/images/logo-blog.png"
```

- El baseurl.

```yml
baseurl                  : "/intro2sd-claudia-torres-cruz-alu0101418285/"
```

- La skin del tema.

```yml
minimal_mistakes_skin    : "sunrise"
```

Además, también se ha añadido:
- La colección `_films`

```yml
  films:
    output: true
    permalink: /:collection/:path/
```

- Un front matter por defecto para esa colección.

```yml
  # _films
  - scope:
      path: ""
      type: films
    values:
      layout: single
      author_profile: false
      comments: true
      related: true  
```

## Uso de Datos Externos (CSV) en _data

Se incluyó un archivo CSV en la carpeta `_data` llamado `best-horror-films.csv` con la información sobre películas de terror. Este archivo contiene los campos Title, Year, Director, Genre, Duration, Description, y las plataformas en las que se encuentran. Una muestra del archivo es:

```csv
Title,Year,Director,Genre,Duration,Description,Prime Video,Disney Plus,HBO Max,Netflix
"The Shining",1980,Stanley Kubrick,Horror,146,"Una familia queda aislada en un hotel embrujado, donde el padre pierde poco a poco la razón.",true,false,true,false
"Halloween",1978,John Carpenter,Horror,91,"Un asesino enmascarado acecha a niñeras en un pueblo suburbano durante la noche de Halloween.",false,true,true,false
```
Para automatizar la presentación de películas en función de su disponibilidad en las plataformas de streaming se ha usado este archivo y Liquid. Dentro de la colección creada anteriormente, `_films`, se ha añadido un archivo que itera sobre la colección de películas y muestra los logotipos de las plataformas en la que está disponible:

```md
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
```
