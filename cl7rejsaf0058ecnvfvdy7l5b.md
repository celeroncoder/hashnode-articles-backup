## Italic Fonts

Making fonts italic in your code editor or your terminal can be hard since there’s not such default visual settings that you can just turn on like to make the fonts bold (only some of them have it). But italic fonts look great and really cool if you have a font that support font ligatures.

## Terminals

Here are some setting to add in your terminal settings to make the fonts go italic.

### Windows Terminal

Open the JSON settings from the settings tab in the terminal


![windows_Terminal.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662541818017/rh7TWfY3L.png align="left")

And add the following settings into that JSON file

```json
"profiles": {
  "list": [
    {
      "font": {
        "face": "VictorMono NF",
        "weight": "bold",
        "axes": {
        	"ital": 1 // this is what does the magic
        }
      },
    },
    ...
  ]
}
```

### Gnome-Terminal

Gnome-Terminal is the default terminal app on most of the Linux distributions, to use italic fonts there’s no additional configuration required, you just need to choose the italic font style from your terminal preferences.

To do that, go to preferences > profile > text > font.

> One thing to note is that you should download the whole font family of the font that you want and then choose the italic font. The italic font style won’t show up if you don’t download the whole font family. So it’s better to download them all.
> 

## VS Code

To make fonts italic in `VSCode` irrespective of your theme, put the following settings into your `settings.json` 

```json
"editor.tokenColorCustomizations": {
    "textMateRules": [
      {
        "scope": [
          "comment",
          "entity.name.type.class", // class names
          "keyword", // import, export, return
          "constant", // String, Number, Boolean..., this, super
          "storage.modifier", // static keyword
          "storage.type.class.js" // class keyword
        ],
        "settings": {
          "fontStyle": "italic bold" // comments are italic
        }
      },
      {
        "scope": [
          "invalid",
          "keyword.operator",
          "constant.numeric.css",
          "keyword.other.unit.px.css",
          "constant.numeric.decimal.js",
          "constant.numeric.json"
        ],
        "settings": {
          // following will be excluded from italics (VSCode has some defaults for italics)
          "fontStyle": "bold"
        }
      }
    ]
  },
```

The above settings does make the following things italic

- class names
- keywords
- constants
- memory modifiers and class keyword

Also, it exempts the custom italic style to certain things that VS Code has default italic config for.

Example Code with Italic Fonts


![italic_font_code.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662541829281/Plab1Vu1w.png align="left")

### Credits

- [GitHub Page](https://github.com/kosimst/FiraFlott)
- [StackOverflow Question](https://stackoverflow.com/questions/41320848/how-do-i-get-visual-studio-code-to-display-italic-fonts-in-formatted-code)