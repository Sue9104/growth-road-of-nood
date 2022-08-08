# Image



| Tools      | Content                   | Website                                                                                                                  |
| ---------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Graphvi    | DOT autoflow chart        | [https://graphviz.gitlab.io/doc/info/lang.html](https://graphviz.gitlab.io/doc/info/lang.html)                           |
| EndrawMax  | GUI                       |                                                                                                                          |
| ImageMagic | Processing pictures & CMD | [https://imagemagick.org/script/command-line-processing.php](https://imagemagick.org/script/command-line-processing.php) |

## ImageMagic

```
// install
sudo apt-get install imagemagick

// format: jpg, png, git, bmp
convert  xxx.jpg  xxx.png

// size change
convert -resize 1024x768  xxx.jpg   xxx1.jpg 
convert -sample 50%x50%  xxx.jpg  xxx1.jpg  
convert -rotate 270 sky.jpg sky-final.jpg 

// add font
convert -fill black -pointsize 60 -font helvetica -draw 'text 10,80 "Hello, World!" ‘  hello.jpg  helloworld.jpg

```
