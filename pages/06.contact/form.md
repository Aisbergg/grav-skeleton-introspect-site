---
title: Contact Us
banner:
  title: Contact Us
  subtitle: "Aliquam ut ex ut interdum donec amet imperdiet eleifend<br>Banner Image: <a href=\"http://www.freepik.com\">Designed by jannoon028 / Freepik</a>"
  image: banner.jpg
menu: Contact
form:
  name: contact-form
  action: /contact
  fields:
    - name: name
      id: name
      label: Name
      outerclasses: 12u$
      placeholder: Enter your name
      autocomplete: on
      type: text
      validate:
        required: true

    - name: email
      id: email
      outerclasses: 12u$
      label: Email
      placeholder: Enter your email address
      type: email
      validate:
        rule: email
        required: true

    - name: message
      label: Message
      outerclasses: 12u$
      size: long
      placeholder: Enter your message
      type: textarea
      validate:
        required: true

  buttons:
    - type: submit
      value: Submit
      classes: btn btn-primary btn-block

  process:
    - email:
        from: "{{ config.plugins.email.from }}"
        to:
          - "{{ config.plugins.email.from }}"
          - "{{ form.value.email }}"
        subject: "[Feedback] {{ form.value.name|e }}"
        body: "{% include 'forms/data.html.twig' %}"
    - save:
        fileprefix: feedback-
        dateformat: Ymd-His-u
        extension: txt
        body: "{% include 'forms/data.txt.twig' %}"
    - display: thankyou

---
