# press-enter

BBS-style ANSI color enter prompts for Node.js modules or the CLI

![image](https://raw.githubusercontent.com/bertrandom/press-enter/gh-pages/demo.gif?token=AADhqoKGfu2hLP1aKjK_4HMixSzjJOqHks5UsL_LwA%3D%3D)

There are 9 animated prompts and 6 static prompts.

The animated prompts were ported from an old PCBoard PPE ([EPE1PWA.ZIP](http://cd.textfiles.com/ppes/E/EPE1PWA.ZIP)) originally released on February 17, 1994, a little over twenty years ago.

![image](https://raw.githubusercontent.com/bertrandom/press-enter/gh-pages/file_id.diz.png?token=AADhqoCAMsJkccmD3dtVn7DCQh0bIRlXks5Utb_swA%3D%3D)

The static prompts were extracted from the default install of Iniquity BBS software v1.01, released on July 26, 1997.

![image](https://raw.githubusercontent.com/bertrandom/press-enter/gh-pages/iniquity.png?token=AADhqhBw0G3Ph5HArbqN5PvFlUZmqzG2ks5UtcH2wA%3D%3D)

Here's are the prompts in use in their corresponding software:

### Animated prompt in PCBoard

![image](https://raw.githubusercontent.com/bertrandom/press-enter/gh-pages/pcboard.gif?token=AADhqjAEFvqOYi_TYGxf5JRBUc4VG8snks5UtcNFwA%3D%3D)

### Static prompt in Iniquity

![image](https://raw.githubusercontent.com/bertrandom/press-enter/gh-pages/iniquity_enter.png?token=AADhqrwlVRFaE_ni7rzEE5yHTEjt6NO0ks5UtcJNwA%3D%3D)

# Installation

`npm install -g press-enter`

# Usage

## CLI usage

```
press-enter [style] [color]
  style: 0-13
  color: red, yellow, green, blue, cyan, magenta, grey
```

For example, if you want to use the 4th prompt in Red, you can type

```
press-enter 4 red
```

or specify that in your shell scripts.

0-8 are animated prompts, 9-13 are static.

Running `press-enter` by itself will default to the 3rd style in the color blue.

## Node usage

You can use `press-enter` anywhere where you want to control flow. The callback fires after the user presses enter.

### pressEnter([options], callback)

Options is an optional hash, you can omit it:

```
var pressEnter = require('press-enter');

pressEnter(function() {
	process.exit();
});
```

| Option | Description |
| ------------ | ------------- |
| style | Style from 0-13, 0-8 are animated, 9-13 are static |
| color | red, yellow, green, blue, cyan, magenta, grey. Defaults to blue. |
| centered | Whether or not to try to detect the number of columns in the terminal and center the prompt. Defaults to true. |
| input | Node.js stream, defaults to stdin |
| output | Node.js stream, defaults to stdout |

Example specifying options:

```
var pressEnter = require('press-enter');

pressEnter({style: 3, color: red}, function() {
	process.exit();
});
```