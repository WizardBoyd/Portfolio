---
title: "Journey Through The Mountain"
date: 2022-12-09T19:53:33+05:30
draft: false
author: "Luis Boyd"
badges:
    - "CSharp"
    - "MonoGame"
    - "WPF"
image: /projects/JTTM_Cover.png
description: "A 2D platformer game about scaling down a magical Mt.Everest "
links:
          - icon: fab fa-github
            url: https://github.com/WizardBoyd/Journey-Through-The-Mountain
toc: true
mathjax: true
---
## Introduction

Journey through the mountain is a game I developed for my 2nd year 2nd semester at staffordshire university.

the story behind the development descsion to use Monogame and c# compared to off the shelf game engine such as unity or unreal was I wanted to familurise myself with a typical game loop and game flow.

## Status

The current status of the project is currenty on hold it has a couple of issues still such as the falling mechanic not working quite right and the obvious screen resolution issue, I may re-write the game in a different framework when I revist it.

## Summary of work

I was the solo developer of the game, I planned level's, wrote character interaction, integrated art assets into the game some of the technical work I did were these:

- wrote game loop
- wrote importer for art assets .png, .wav
- wrote node editor for character text flow
- wrote a level editor to iterate through different level designs
- wrote collision system
- implemented enemey simple movement AI
- implemented an animation system

## Journey through the mountain - playthrough video

{{< youtube g6L4weujXPY >}}

# More Details On Development

if you want to know more details keep reading I go over:
- tools I developed

## Level Editor 
{{< youtube L6dnDOCIKUE >}}

the level editor read and wrote the level details in a binary format which was put into a .Map file which I then wrote an importer to handle loading that data which would build the tiles and all the "event blocks"

![MapFilesPng](/projects/MapFiles.png)

the tiles were all preloaded into the editor based on tilesets that were in the game so as soon as I added in a new tileset into the game it would appear in the editor.

essentially all the data structure was for each layer it was a 2d array of tile codes that when parsed read the correct tile from memory and placed it in the correct location in the world space.

"Event blocks" were positions in the world where on level loading they would spawn either a collidable event or a entity itself. if it was a collidable event then it would fire off some delegate after it was collided with by the player.

the red blocks tint on some of the blocks indicated which tiles where collidable as I wanted the player to be able to walk behind/in front of tiles but also have it so there was collision still so I handled that seperatly with these tint indications.

