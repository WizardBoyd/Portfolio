---
title: 'Math Basics - Unity Clock'
date: 2024-06-13T22:50:23+01:00
draft: false
author: "Luis Boyd"
tags:
 - Beginer Math
 - Unity
 - Game Development
image: /images/UnityClock.png
description: "I go through the math's behind what makes a clock tick including the positioning of the handles and basic triganometry."
mathjax: true
---

# Introduction

I go through the math's behind what makes a clock tick including the positioning of the handles and basic triganometry.


## Inspiration

The inspiration for this post came from a blog article by [CatlikeCoding](https://catlikecoding.com/unity/tutorials/basics/game-objects-and-scripts/) on basic game objects in unity.

I wanted to document my expirence and what I learnt by going through this

## Trigonometry


before going through this guide I knew about concepts like cos(x) and sin(x), however I had no clue on how they related to other concepts such as circles/angles/etc..

after going through the guide I have gained a better understanding of these basic trigonometry functions

![UnitCircleGif](/images/blogs/MathUnitCirlceGeogabra.gif)

$$\[ \theta = (90 - 30i) \left(\frac{\pi}{180}\right) \]$$
The angle (or theta) is offset by 90 so it starts at the 12/midnight handle this converts the angle to a usable radian value.

The X and Y values can then be calculated given the angle at a certain interval.

$$\[ x_i = R \cos(\theta) \]
\[ y_i = R \sin(\theta) \]$$

which gives us the vector position of.
$$\\mathbf{v} = \langle x_i, y_i \rangle\$$

# Unity
![UnityClockPlayGif](/images/blogs/UnityClockPlay.gif)

Now that I had figured out the core math concepts behind how find out the vector when given a angle for the clock it was time to implement the C# code for the object

```c#

using System.Collections.Generic;
using UnityEngine;

public class Clock : MonoBehaviour
{
    [SerializeField] 
    private Transform _hoursPivot;
    [SerializeField] 
    private Transform _minutesPivot;
    [SerializeField] 
    private Transform _secondsPivot;

    [SerializeField] 
    private int ClockMarks;
    [SerializeField] private float ClockRadius = 4f;

    private TimeSpan CurrentDateTime;

    private float hoursToDegress = 0.0f;
    private float minutesToDegress = 0.0f;
    private float secondsToDegress = 0.0f;

    private void Awake()
    {
        hoursToDegress = (360f / ClockMarks);
        minutesToDegress = (360f / 60f);
        secondsToDegress = (360f/60f);
        RotateHandles_Hour();
        RotateHandles_Minutes();
        RotateHandles_Seconds();
    }
    

    private Quaternion GetAngleForClock(float pos)
    {
        //the clock face
        pos = Mathf.Abs(pos % 12);
        float angle = (0 - 30 * pos);
        // float angleInRadians = angle * Mathf.PI / 180;
        // float xPos = ClockRadius * Mathf.Cos(angleInRadians);
        // float yPos = ClockRadius * Mathf.Sin(angleInRadians);
        return Quaternion.Euler(0,0,angle);
    }

    private void RotateHandles_Hour()
    {
        _hoursPivot.localRotation = Quaternion.Euler(0,0,-hoursToDegress*(float)CurrentDateTime.TotalHours);
    }
    private void RotateHandles_Minutes()
    {
        _minutesPivot.localRotation =  Quaternion.Euler(0,0,-minutesToDegress * (float)CurrentDateTime.TotalMinutes);
    }
    private void RotateHandles_Seconds()
    {
        _secondsPivot.localRotation =  Quaternion.Euler(0,0,-secondsToDegress * (float)CurrentDateTime.TotalSeconds);
    }

    private void Update()
    {
        CurrentDateTime = DateTime.Now.TimeOfDay;
        RotateHandles_Hour();
        RotateHandles_Minutes();
        RotateHandles_Seconds();
    }
}

```

the only change I made here was instead of using radians which I had been working in with GeoGebra I used angle's and utilised unity's Quaternion struct to convert between euler and quaternion.

using unity's update loop and .Net DateTime to work out the current hosts system time I made a functioning clock.

# Future Ideas
- make a 24-hour clock
- animate an object by moving them along a circular spline