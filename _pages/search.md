---
permalink: /search/
title: Buscar
---

{% capture initSearch %}

<form id="search-form">
  <label for="search">Buscar término (se aceptan regex):</label>
  <input id="search" type="text" placeholder="ej halloween" autocomplete="off" autofocus />
  <ul id="list"></ul>
</form>

<script type="text/javascript" src="{{site.baseurl}}/assets/src/search.js"></script>
<script type="text/javascript" src='{{site.baseurl}}/assets/src/fetch.js'></script>

<script type="text/javascript">
    const search = new JekyllSearch({
        dataSource: '{{site.baseurl}}/assets/src/search.json',
        searchField: '#search',
        resultsList: '#list',
        siteURL: '{{site.baseurl}}' 
    });
    search.init();
</script>

<noscript>Por favor permite JS para que el formulario funcione.</noscript>

{% endcapture %}

{{ initSearch | lstrip }}