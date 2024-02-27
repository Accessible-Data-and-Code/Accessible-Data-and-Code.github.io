---
# Leave the homepage title empty to use the site title
title:
date: 2022-10-24
type: landing

sections:
  - block: slider
    content:
      slides:
      - title: Jupyter4Science
        content: Jupyter4Science is a **knowledge base** that contains original content and curated resources about developing and sharing Jupyter Notebooks as they are used in the context of scientific applications.
        align: center
        background:
          image:
            filename: random.jpeg
            filters:
              brightness: 0.7
          position: right
          color: '#666'
        link:
          icon: graduation-cap
          icon_pack: fas
          text: About
          url: ../about/
        
    design:
        # Slide height is automatic unless you force a specific height (e.g. '400px')
        slide_height: ''
        is_fullscreen: true
       
          
  - block: collection
    content:
      title: Latest News
      subtitle:
      text:
      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: posts
    design:
      view: card
      columns: '2'
      card_style: small
      
  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
      

---