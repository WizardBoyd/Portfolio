---
title: "Network Exploration Project"
date: 2023-06-17T19:53:33+05:30
draft: false
author: "Luis Boyd"
badges:
    - "C++"
    - "SDL2"
    - "TCP/UDP"
    - "Networking"
    - "Multiplayer"
image: /projects/MouseCatNetwork_Cover.png
description: "A Simple Game that showcases off Socket Programming"
links:
          - icon: fab fa-github
            url: https://github.com/WizardBoyd/NetworkingExplorationProject
toc: true
mathjax: true
---
## Introduction

This was a project I developed during off times after my 2nd year at university along side my placement year, I followed a lot of concepts from Multiplayer Game Programming: Architecting Networked Games (Game Design) by Josh Glazer and Sanjay Madhav and Programming Multiplayer Games by Andrew Mulholland and Teijo Hakala

## Status

The Current Status of this project is complete as it was only meant to showcase off simple socket programming concepts so I don't intend to take this game idea further

## Summary of work

Most of the work done was expiremental with getting myself familur with socket programming but I learned these concepts:

- TCP/IP Internet Model (and the OSI model)
- Berkeley Sockets
- Object Serialization
- Object Replication
- Client/Server Topology Model
- SDL2 Game Implementation
- Socket Polling
- TCP/UDP Protocols
- Reliable UDP

## Networking Project Example - playthrough video

{{< youtube aN0Dj2xEfWw >}}

<!-- # More Details On Development

if you want to know more details keep reading I go over:
- tools I developed

## Level Editor 
{{< youtube L6dnDOCIKUE >}}

the level editor read and wrote the level details in a binary format which was put into a .Map file which I then wrote an importer to handle loading that data which would build the tiles and all the "event blocks"

![MapFilesPng](/projects/MapFiles.png)

the tiles were all preloaded into the editor based on tilesets that were in the game so as soon as I added in a new tileset into the game it would appear in the editor.

essentially all the data structure was for each layer it was a 2d array of tile codes that when parsed read the correct tile from memory and placed it in the correct location in the world space.

"Event blocks" were positions in the world where on level loading they would spawn either a collidable event or a entity itself. if it was a collidable event then it would fire off some delegate after it was collided with by the player.

the red blocks tint on some of the blocks indicated which tiles where collidable as I wanted the player to be able to walk behind/in front of tiles but also have it so there was collision still so I handled that seperatly with these tint indications. -->

