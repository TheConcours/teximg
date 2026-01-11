Original Repo <https://github.com/wuqui/teximg>

This is a Quarto filter that allows you to use LaTeX code in your Quarto documents and render them to different formats, such as PDF, HTML, or DOCX.
(Only tested in revealjs)

# Major change from the original repo

- XeLaTeX -> LuaLaTeX
- svg -> png (pdf2svg -> Imagemagick)

# To-Dos

- Implement image width (Now it's fixed to be 50%)

# Requirements and configuration

- Image magick is required
- install this filter using `quarto add TheConcours/teximg`
- activate it using

  ```yml
  filters:
    - teximg
  ```

- if you have any LaTeX requirements, add them to a `preamble.sty` file in your quarto folder

# Functionality

Here is a diagram using the LaTeX’s `forest` library:

````md
```{=tex}
\begin{forest}
  [one
    [two]
    [three]
  ]
\end{forest}
```
````

When rendering to PDF via LaTeX, this filter passes the code on to the LaTeX process.

When rendering to other formats, the filter:

- checks if the image file has already been produced; if not:
- produces a standalone PDF of this block,
- converts it to png using imagemagick,
- inserts this image in the output file.
