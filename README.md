# Grav-collection
A collection of useful Grav templates

### Schema.org microdata for article page
```
    <script type="application/ld+json">
      {
        "@context": "http://schema.org",
        "@type": "NewsArticle",
        "headline": "{{ page.title }}",
        "author": "{{ page.author }}",
        "dateModified": "{{ page.modified|date("Y-m-d") }}",
        "articleBody": "{{ page.content|e }}",
        "publisher": {
          "@type": "Organization",
          "logo": {
          "@type": "ImageObject",
          "url": "{{base_url_absolute}}URL_LOGO"
                   },
         "name": "ORGANIZATION_NAME"
                     },
        "datePublished": "{{ page.date|date("Y-m-d") }}T{{ page.date|date("H:i") }}",
        "image": {
         "@type": "ImageObject",
         "height": "350",
         "width": "550",
         "url": "{{ base_url_absolute }}{{ page.media.images|first.url}}"
                 }
      }
    </script>
```

### Basic AMP Page

#### Configuration

In Configuration -> Media , add a file extension and fill fields as below:

File Extension: amp
Type: file
Thumb: media/thumb-amp.png
Mime Type: text/html
Image options: 


In your base.html.twig, add

```
{% if page.template == "YOURTEMPLATE" %}
        <link rel="amphtml" href="{{page.url}}.amp">
{% endif %}
```

Then, you can create partials/base.amp.twig

```
<!doctype html>
<html amp lang="fr">
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="canonical" href="{{ page.url }}" />
    <meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
        <script type="application/ld+json">
      {
        "@context": "http://schema.org",
        "@type": "NewsArticle",
        "headline": "{{ page.title }}",
        "author": "{{ page.author }}",
        "dateModified": "{{ page.modified|date("Y-m-d") }}",
        "articleBody": "{{ page.content|e }}",
        "publisher": {
          "@type": "Organization",
          "logo": {
          "@type": "ImageObject",
          "url": "{{base_url_absolute}}URL_LOGO"
                   },
         "name": "ORGANIZATION_NAME"
                     },
        "datePublished": "{{ page.date|date("Y-m-d") }}T{{ page.date|date("H:i") }}",
        "image": {
         "@type": "ImageObject",
         "height": "350",
         "width": "550",
         "url": "{{ base_url_absolute }}{{ page.media.images|first.url}}"
                 }
      }
    </script>
    <style amp-boilerplate>body{-webkit-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-moz-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-ms-animation:-amp-start 8s steps(1,end) 0s 1 normal both;animation:-amp-start 8s steps(1,end) 0s 1 normal both}@-webkit-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-moz-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-ms-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-o-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}</style><noscript><style amp-boilerplate>body{-webkit-animation:none;-moz-animation:none;-ms-animation:none;animation:none}</style></noscript>
      

    <script async custom-element="amp-analytics"
    src="https://cdn.ampproject.org/v0/amp-analytics-0.1.js"></script>
    <script async src="https://cdn.ampproject.org/v0.js"></script>
  </head>
  <body>
      <amp-analytics type="googleanalytics">
<script type="application/json">
{
  "vars": {
    "account": "UA-YOURANALYTICSCODE"
  },
  "triggers": {
    "trackPageview": {
      "on": "visible",
      "request": "pageview"
    }
  }
}
</script>
</amp-analytics>
      <h1>{{ page.title }}</h1>
    {% block content %}{% endblock %}
  </body>
</html>

```
