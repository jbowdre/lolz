# John's lolz

This repo holds miscellaneous stuff I cobbled together for use with my [omg.lol profile](https://jbowdre.lol) and [associated services](https://home.omg.lol/referred-by/jbowdre).

### Tempest
I was inspired by another omgloler who had their local live weather conditions displayed on their profile page, but I didn't want to put my weather station identifier or API token in the client-side code of my page. So I implemented a sort of API proxy: a [simple GitHub Action workflow](.github/workflows/tempest.yml) that runs every ~5 minutes. It uses secrets stored securely in the repo to fetch the weather data from the [Weatherflow Tempest API](https://weatherflow.github.io/Tempest/api/), filters for just the current conditions data (not the giant mess of future-forecast details), and posts that to my [paste.lol pastebin](https://paste.jbowdre.lol/tempest.json).

I can then safely use client-side scripting to retrieve the weather details from the pastebin. I cobbled together a quick [test HTML page](tempest.html) that I could use for local testing/development as I worked through how to get the data displayed and formatted correctly.

![Plain, unstyled weather test page](assets/weather-plain.png)

And then I just copied/pasted the `<script />` and relevant `<span />` sections to the omg.lol profile page editor, and made a few tweaks to better fit the existing schema. I'm pretty pleased with how it turned out!

![Groovy styled weather displayed on my profile page](assets/weather-styled.png)