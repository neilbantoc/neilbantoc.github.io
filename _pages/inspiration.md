---
layout: inspiration
title: inspiration
permalink: "/inspiration/"
---
<link href="{{ site.url }}/css/inspiration.css" media="screen, projection" rel="stylesheet" type="text/css"/>

<div id="quote-container">
  <div id="quote-backdrop">
    <div class="small-3"></div>
     <div id="quote-block" class="small-9">
        <p id="quote"></p>
        <span><span id="quote-author"></span> | <a id="quote-link"></a></span>
        <br/> <br/>
        <button id="quote-new" class="waves-effect waves-light btn" onclick="changeQuote()">Next</button>
    </div>
  </div>
</div>

{% include jquery.html %}

<script>
  var inspirations = null;
  var index;

  var changeQuote = function () {
    console.log(inspirations);

  index = (index + 1) % inspirations.length;

    var selectedQuote = inspirations[index];

    var withQuotes = "“" + selectedQuote.quote + "”";

    $("#quote").text(withQuotes);
    $("#quote-author").text(selectedQuote.author);
    $("#quote-link").attr("href", selectedQuote.link)
    .text(selectedQuote.title);

    if (selectedQuote.image != null) {
        $("#quote-container").css('background-image', 'url(' + selectedQuote.image + ')')
    }
  };

  var quotesLoaded = function (data) {
    console.log(data);
    inspirations = data;
    index = Math.floor(Math.random() * inspirations.length);
    changeQuote();
  };

  var jsonData = $.getJSON("{{$site.url}}/json/inspiration.json", quotesLoaded);
</script>
