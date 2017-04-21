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
