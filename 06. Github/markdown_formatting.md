# Markdown formatting in github

## General documentation 

[github website](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#headings)

[Markdown cheatsheet](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/markdown-cheatsheet.pdf)

## Add summary/details section 

```
<details><summary>My summary</summary>
<p>
My details
</p>
</details>
```

## Add link

```
[Markdown cheatsheet](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/markdown-cheatsheet.pdf)
```


## Add images 

```
![image_name](image_link)
```

```
<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/ls_l.png" width="500"></p>
```


## Add notes

```
> mynote
```


## Add footnotes

```
Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].  

You can also use words, to fit your writing style more closely[^note].

[^1]: My reference.
[^2]: Every new line should be prefixed with 2 spaces.  
  This allows you to have a footnote with multiple lines.
[^note]:
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.
```


