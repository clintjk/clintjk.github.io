---
title: "Learning how to use Hugo"
date: 2023-06-15T17:30:57+01:00
draft: false
showAuthor : true
---
I have been trying to learn how to create and use a static website to encourage myself to learn and write about projects I work on. My quest started with a site made using the [Jekyll](https://jekyllrb.com/) static site generator and its built-in integration with github pages. This worked for a while but since I didn't really research how best to use it and add content, it ended up sitting on GitHub gathering dust.

Now, a year or so later, I've started afresh with [Hugo](https://gohugo.io/) (basically Jekyll but apparently faster) and i've established a simple yet effective workflow

## Editing

There are a multitude of markdown editors to choose from to write content with which makes my choice of using [Sublime Text](https://www.sublimetext.com/) a little strange. It is, however, the only editor that I have experience using that has plugins made for by the Hugo community, that makes it very easy to use in conjuction with a Hugo site.

### Configuring Sublime Text

First [install](https://www.sublimetext.com/download) Sublime Text

Then install Package Control. This is sublime text's own package manager which is used to install plugins. 

Open the command palette: on Mac its <kbd>CMD</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> or on Windows use <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> 

type `install package control` and press enter

Once thats done, we can add plugins. I am using [Hugoify](https://github.com/akmittal/Hugofy-sublime) which makes adding content and using Hugo easy by bringing hugo commands into Sublime Text. Using shortcuts, we can add content, build, set themes and start a local server.

Usually this would be done using the command palette and typing `install hugoify`, however i've found that the latest version installable from package control has some bugs so instead we'll go to the hugoify github, download the repo and extract it to the packages folder for Sublime Text. 

You can open the folder by typing `preferences: browse packages` in the command palette. Place the plugin folder here and it's installed.

Now open the hugoify folder and edit the settings file appropriately. This is what mine looks like:

```
{
	//root directory for hugo websites use double backwork slash for windows
	//e.g. windows C:\\Users\\myusername\\
	//e.g. Linux/Mac /home/myusername
	"Directory": "/Users/clint",
	"Server":
	{
		"PORT": 8000, //server port number
		"THEME_FLAG": false, //use `--theme` flag
		"DRAFTS_FLAG": false, //use `--buildDrafts` flag
		"THEME": "bootstrap" //theme used by `--theme` flag
	},
	//website name
	"Sitename": "clintjk.github.io"  
}
```

Once thats done we can type `hugoify` into the command palette to see what commands we can use.

### Writing Posts

Now by running `hugoify: new post` we can type in the type of post and it's name, and a new post will be generated with the default front matter, which we can then edit. We can change the default front matter set by editing the `default.md` file found in the archetypes folder of our Hugo site.

This is what mine looks like:

```md
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
showAuthor : true
---
```

## Saving

Now all we need to do is update our github repo from our local repo after adding new content:

```
git commit -a -m "Added new post!"
git push
```

## Notes

Of course this workflow is probably going to change and become more sophisticated - depending on what I want to do with the website. But for now, it is quite efficient

[Hugoify](https://github.com/akmittal/Hugofy-sublime) is made by Amit Mittal [Amit Mittal](https://github.com/akmittal)



