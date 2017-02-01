---
layout: default
title: resume
permalink: "/resume/"
---
<link href="{{ site.github.url }}/css/resume.css" media="screen, projection" rel="stylesheet" type="text/css">


<div id="resume"> </div>


<script type="text/javascript" src="{{site.url}}/js/pdfobject.js"></script>
<script>
  var options = {
      width: "100%",
      height: "100%",
      fallbackLink: "<a href='{{ site.github.url }}/assets/resume.pdf'><h1>Click to open</h1></a>",
      pdfOpenParams: { view: 'FitV'}
  };
  PDFObject.embed("{{site.url}}/assets/resume.pdf", "#resume", options);
</script>
