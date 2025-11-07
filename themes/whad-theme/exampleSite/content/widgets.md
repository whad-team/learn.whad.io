+++
title = 'Widgets'
date = 2024-12-18T16:00:10+01:00
draft = false
description = "This is a test page"
author = "Romain Cayre"
type = "page"
color = "pink"
icon = "fa-solid fa-keyboard"
width = 6
+++
# Listes

* element 1
* element 2
    * element 2.a
    * element 2.b
    * element 2.c
* element 3
    * element 3.a
    * element 3.b
    
# Lien

* My super cool link is <https://www.google.fr>

* Check my [website](https://www.google.fr)

# Boxes
## Info box

* Simple info box:
{{< info >}}
Simple info box
{{< /info >}}


* Simple info box with custom title:
{{< info title="Custom title">}}
Simple info box with title
{{< /info >}}


## Warning box

* Simple warning box:
{{< warning >}}
Simple warning box
{{< /warning >}}


* Simple warning box with custom title:
{{< warning title="Custom title">}}
Simple warning box with title
{{< /warning >}}



## Danger box

* Simple danger box:
{{< danger >}}
Simple danger box
{{< /danger >}}


* Simple danger box with custom title:
{{< danger title="Custom title">}}
Simple danger box with title
{{< /danger >}}



## Success box

* Simple success box:
{{< success >}}
Simple success box
{{< /success >}}


* Simple success box with custom title:
{{< success title="Custom title">}}
Simple success box with title
{{< /success >}}


# Buttons

## Solutions


* Simple solution button:
{{< solution >}}
Simple solution button
{{< /solution >}}


* Simple solution box with custom title:
{{< solution title="Custom title">}}
Simple solution button with title
{{< /solution >}}

## Link button

* Basic button

{{< button href="/" >}}
Simple button with a link
{{< /button >}}


* Basic button with custom icon

{{< button href="/" icon="fa-solid fa-atom">}}
Simple button with a link & a custom icon
{{< /button >}}


* Basic button with custom icon and other color

{{< button href="/" icon="fa-solid fa-atom" color="orange">}}
Simple button with a link, a custom icon & a custom color
{{< /button >}}

# Code snippet

* Raw snippet (inline): ```this is a code snippet``` and you can continue your text after.

* Raw snippet (block)
```
This is a 
raw
snippet of code
```

* Code snippet with syntax-highlighting (block)
```python
print("This is a") 
print("raw")
for i in range(0, 12):
    print("snippet of code")
```

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    for (int i=0;i<12;i++) {
        printf("i=%d\n", i);
    }
    return 0;
}
```

```ada
with Ada.Text_IO; -- Bibliothèque

-- Déclaration de la procédure "Hello"
procedure Hello is
begin
  -- Imprimer "Hello, world!" à l'écran
  Ada.Text_IO.Put_Line("Hello, world!");
end Hello;
```

# Images

* Simple image

![miaou](/miaou.png "Miaou")

* Simple centered image
{{< center >}}
![miaou](/miaou.png "Miaou")
{{< /center >}}
