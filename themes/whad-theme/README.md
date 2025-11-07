# INSA Hugo theme

## Get the theme

Install [Hugo](https://gohugo.io/installation/) and **[dart-sass](https://gohugo.io/functions/resources/tocss/#dart-sass)**.

Import the theme:
```
git clone https://github.com/RCayre/insa-hugo-theme themes/insa-hugo-theme
```

and add it in `config.toml`:
```toml
theme = 'insa-hugo-theme'
```

## Configuration

Configure base URL, language, title, description, website icon and author informations in your `config.toml`:

```toml
baseURL = 'https://example.org/'
title = "Site d'exemple"
theme = 'insa-hugo-theme'
description = 'Ceci est un template de base'

languageCode = 'fr'
DefaultContentLanguage = "fr"

[params.icon]
collection = 'fa-solid'
icon = 'fa-laptop'

[params.author]
name = "Romain Cayre"
email = "cayre@insa-toulouse.fr"
institution = "INSA Toulouse"
```

## Add a new content page

You add a new page with:
```
hugo new page1.md
```

In the configuration header of your page, provide icon, box width and background color. It will be automatically added to the home page according to your parameters:
```
+++
title = 'About'
date = 2024-12-18T16:00:10+01:00
draft = false
description = "This is a test page"
author = "Romain Cayre"
type = "page"
color = "red"
icon = "fa-solid fa-earth"
width = 12
+++
```
Be careful, you need to indicate ```draft = false``` to take the new page into account during the generation.

## Configure the home page

To add information to the homepage, create a **_index.md** file in the content directory and provide the following information in the header:
```
+++
title = 'Home'
date = 2024-12-18T16:00:10+01:00
draft = false
description = "Description de la page d'accueil"
author = "Romain Cayre"
type = "grid"
color = "blue"
icon = "info"
+++
```
The content will be displayed above the grid on the homepage.

## Widgets
You can use various widgets in the content:


### Boxes
#### Info box

* Simple info box:
```
{{< info >}}
Simple info box
{{< /info >}}
```

* Simple info box with custom title:
```
{{< info title="Custom title">}}
Simple info box with title
{{< /info >}}
```

#### Warning box

* Simple warning box:
```
{{< warning >}}
Simple warning box
{{< /warning >}}
```

* Simple warning box with custom title:
```
{{< warning title="Custom title">}}
Simple warning box with title
{{< /warning >}}
```


#### Danger box

* Simple danger box:
```
{{< danger >}}
Simple danger box
{{< /danger >}}
```

* Simple danger box with custom title:
```
{{< danger title="Custom title">}}
Simple danger box with title
{{< /danger >}}
```


#### Success box

* Simple success box:
```
{{< success >}}
Simple success box
{{< /success >}}
```

* Simple success box with custom title:
```
{{< success title="Custom title">}}
Simple success box with title
{{< /success >}}
```

### Buttons

#### Solutions


* Simple solution button:
```
{{< solution >}}
Simple solution button
{{< /solution >}}
```

* Simple solution box with custom title:
```
{{< solution title="Custom title">}}
Simple solution button with title
{{< /solution >}}
```
#### Link button

* Basic button
```
{{< button href="/" >}}
Simple button with a link
{{< /button >}}
```

* Basic button with custom icon
```
{{< button href="/" icon="fa-solid fa-atom">}}
Simple button with a link & a custom icon
{{< /button >}}
```

* Basic button with custom icon and other color
```
{{< button href="/" icon="fa-solid fa-atom" color="orange">}}
Simple button with a link, a custom icon & a custom color
{{< /button >}}
```

### Images

* Simple image
```
![miaou](/miaou.png "Miaou")
```

* Simple centered image
```
{{< center >}}
![miaou](/miaou.png "Miaou")
{{< /center >}}
```
