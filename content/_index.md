---
# Leave the homepage title empty to use the site title
title:
date: 2023-09-01
type: landing

sections:
  - block: hero
    content:
      title: |-
        AI Safety Unconference & EAGxAustralia 2023
      image:
        filename: eagx_aus_logo.jpg
      text: |-
        <br>

        I'll be at the AI Safety Unconference and then EAGxAustralia from 22-24 September 2023. Please reach out via Swapcard if you're attending - I'm keen to connect and talk AI safety, policy & governance.

        <br>
      cta:
        label: Get involved
        url: 'https://forms.gle/6BEMc3DYuU52yfGn8'
        icon_pack: fas
        icon: star
      cta_alt:
        label: AI governance opportunities in Australia
        url: 'https://docs.google.com/document/d/1TRfgYpy8dOTXU_KJpqq1ZkBIUKqpyOaW6vBqufpRqGw/edit'
  - block: about.biography
    id: about
    content:
      title: 
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
  - block: portfolio
    id: projects
    content:
      title: Projects
      filters:
        folders:
          - project
      # Default filter index (e.g. 0 corresponds to the first `filter_button` instance below).
      default_button_index: 0
      # Filter toolbar (optional).
      # Add or remove as many filters (`filter_button` instances) as you like.
      # To show all items, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the toolbar, delete the entire `filter_button` block.
       # buttons:
       # - name: All
       #   tag: '*'
       # - name: Research
       #   tag: research
       # - name: Behaviour science
       #   tag: behaviour science
       # - name: Complex challenges
       #   tag: complex challenges
    design:
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '1'
      view: compact
      # For Showcase view, flip alternate rows?
      flip_alt_rows: false
  # - block: collection
  #  content:
  #    title: Writing and Talks
  #    text: 
  #    filters:
  #      folders:
  #        - publication
  #      exclude_featured: true
  #  design:
  #    columns: '2'
  #    view: citation
  - block: contact
    id: contact
    content:
      title: Contact
      subtitle:
      text: 
      # Contact (add or remove contact options as necessary)
      email: alexander@aksaeri.com
      phone: +61 405 519 733
      appointment_url: 'https://calendar.app.google/sv3Sb5sjUxxTdssv8'
      # Automatically link email and phone or display as text?
      autolink: true
      design:
      columns: '2'
---
