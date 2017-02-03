---
layout: default
title: inspiration
permalink: "/inspiration/"
---
<link href="{{ site.url }}/css/inspiration.css" media="screen, projection" rel="stylesheet" type="text/css">
<div id="quote-container">
  <div id="quote-block">
      <p id="quote"></p>
      <span><span id="quote-author"></span> | <a id="quote-link"></a></span>
  </div>
</div>

{% include jquery.html %}
<script>
  var changeQuote = function (inspirations) {

    var random = Math.floor(Math.random() * inspirations.length);
    var selectedQuote = inspirations[random];

    var withQuotes = "“" + selectedQuote.quote + "”";

    console.log(withQuotes);

    $("#quote").text(withQuotes);
    $("#quote-author").text(selectedQuote.author);
    $("#quote-link").attr("href", selectedQuote.link)
    .text(selectedQuote.title);
  };

  var inspirations = $.getJSON("{{$site.url}}/json/inspiration.json", changeQuote);
</script>
