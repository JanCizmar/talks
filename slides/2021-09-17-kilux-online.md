---
title: Tolgee: Tool for Web Application Localization Without Tears paginate: true marp: true theme: default
---
<style>
section { 
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
font-weight: 200;
}
h1, h2, h3{
font-weight: 300 !important;
}
h1, h2{
color: #5e203f !important;
}
a {
color: #743455 !important;
}
section pre{
border: 1px solid rgba(226,226,226,0.6);
background-color: rgba(88,50,73,0.03);

}
</style>

![h:100px](images/tolgeeLogo.svg)

## Web Application Localization Without Tears 😢 <!-- fit -->

Jan Cizmar

[tolgee.io/t/2021-09-17-kilux-online.html](https://tolgee.io/t/2021-09-17-kilux-online.html)

---

<h2 style="text-align: center">
   Tolgee is open-source tool simplifying localization process as much as possible
</h2>

---

# Topics
- Common localization process
- The Tolgee way (DEMO)
- ICU message format
- Preparing for production
- Other tools

---
# Common localization process <!-- fit -->
---

## Adding a new text to translate

1. Create translation key in the code

        homepage_hello_world

2. Add the key to the file with localization data or use extraction ➕
3. Translate the key to your mother language ✏️
4. Check it was translated correctly, it looks fine and layout is not broken ✅

---

## Modifying existing translation

1. Find out which key it is 🕵️
2. Open the localization file, and modify the value ✏️
3. Check it was translated correctly, it looks fine and layout is not broken ✅

---

## Letting a translator to translate your app into foreign language

1. Take the localization data from your code & send it to translator
2. Answer a lot of questions about context of the data ⁉️

---

- Muskelkater -> Musclecat
- Wasserhahn -> Waterchicken

- Save -> sparen, anlegen, speichern?

---

<div style="text-align: center">

![beware_of_safety.png](images/beware_of_safety.png)

</div>

---

## Letting a translator to translate your app into foreign language

1. Take the localization data from your code & send it to translator
2. Answer a lot of questions about context of the data ⁉️
3. Get wrong translations because of missing context ❌
4. Append the data to the code

---

<div style="text-align: center">

![image](images/hey_jude.png)

</div>

---

# The Tolgee method

- Developers develop their code 🧑‍💻
- Translators translate 👩‍💻

---

# Localization process with Tolgee (Demo)

---

# Project setup <!-- fit -->

---

# ICU Message Format

```
Hello, I am {name}.
```

name=Peter → Hello, I am Peter.

```
{dogsCount, plural, 
   one {One dog is}
   other {# dogs are}
} here.
```

dogsCount=1 → One dog is here. 

dogsCount=0 → 0 dogs are here. 

dogsCount=2 → 2 dogs are here. 

...

---

```
{gender_of_host, select,
  female {
    {num_guests, plural, offset:1
      =0 {{host} does not give a party.}
      =1 {{host} invites {guest} to her party.}
      =2 {{host} invites {guest} and one other person to her party.}
      other {{host} invites {guest} and # other people to her party.}}}
  male {
    {num_guests, plural, offset:1
      =0 {{host} does not give a party.}
      =1 {{host} invites {guest} to his party.}
      =2 {{host} invites {guest} and one other person to his party.}
      other {{host} invites {guest} and # other people to his party.}}}
  other {
    {num_guests, plural, offset:1
      =0 {{host} does not give a party.}
      =1 {{host} invites {guest} to their party.}
      =2 {{host} invites {guest} and one other person to their party.}
      other {{host} invites {guest} and # other people to their party.}}}}
```

[More about ICU message format (https://tolgee.io/docs/icu_message_format)](https://tolgee.io/docs/icu_message_format)

---

# Translating to new language <!-- fit -->

---
# Preparing App for production <!-- fit -->

---
# Tolgee Architecture

- REST API
- Web application
- SDKs

---

# Single source of truth

- All developers & translators use the same localization data
- The data may but don't have to be stored in VCS

---

# Deployment

<div style="display: flex; width: 100%; text-align: center; margin-top: 50px">
<div style="text-align: center; flex-grow: 1">
Locally
<div style="font-size: 100px; text-align: center">
👤
</div>

    docker run -p8080:8080 tolgee/tolgee

</div>
<div style="text-align: center; flex-grow: 1; margin: 0 40px">
Your cloud infrastructure
<div style="font-size: 100px; text-align: center">
🏢
</div>
<div style="font-size: 20px">

    docker-compose up

</div>
</div>
<div style="text-align: center; flex-grow: 1">
Use Tolgee Cloud
<div style="font-size: 100px; text-align: center">
☁
</div>

[https://app.tolgee.io](https://app.tolgee.io)

</div>
</div>

---

# The Future

- Release stable version in few days

## Features

- Automatic screenshot generation ✅
- Implement enhancements & suggestion from your feedback!
- Glossaries, Translation Memory, Automated translations
- Support for mobile and desktop apps
- Plugins for IDE & Design tools

---

## Technologies

<div style="display: flex; justify-content: space-around; flex-direction: column; margin-top: 50px">
<div style="display: flex; justify-content: space-around">

![width:200px](images/kotlin.png)

![width:200px](images/spring.png)

![width:100px](images/postgres.png)
</div>
<div style="display: flex; justify-content: space-around; margin-top: 30px">

![width:100px](images/typescript.png)

![width:100px](images/react.png)

![width:100px](images/material.png)

</div>
<div style="display: flex; justify-content: space-around; margin-top: 30px">

![width:100px](images/docker.png)

![width:100px](images/kubernetes.png)

</div>
</div>

---

# Proprietary tools

- Crowdin
- Lokalise
- Phrase
- Many more

# Open-source

- Weblate
- Pontoon

---
<div style="display: flex">
<div>

## Docs

https://tolgee.io

## Contact me

cizmar@tolgee.io

## Github projects

<div style="display: flex">

[github.com/tolgee/server](https://github.com/tolgee/server)
<div style="margin-left: 10px">
<!-- Place this tag where you want the button to render. -->
<a style="margin-left: 20px" class="github-button" href="https://github.com/tolgee/server" data-icon="octicon-star" data-size="large" aria-label="Star tolgee/server on GitHub">Star</a>
</div>
</div>
<div style="display: flex">

[github.com/tolgee/tolgee-js](https://github.com/tolgee/tolgee-js)
<!-- Place this tag where you want the button to render. -->
<div style="margin-left: 10px">
<a class="github-button" href="https://github.com/tolgee/server" data-icon="octicon-star" data-size="large" aria-label="Star tolgee/server on GitHub">Star</a>
</div>
</div>

## Slides

[tolgee.io/t/2021-09-17-kilux-online.html](https://tolgee.io/t/2021-09-17-kilux-online.html)

</div>
<div style="display: flex; flex-grow: 1; justify-content: center; align-items: center">

![w:400px](images/tolgeeLogo.svg)

</div>
</div>
<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>
