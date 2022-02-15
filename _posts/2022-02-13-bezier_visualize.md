---
title: "Visualizing Bézier Curves"
tags: 
    - Bézier-Curves
    - Visualization
category:
    - Visualization
date: 2022-02-13
toc: false
layout: single
classes: wide
# link: https://koushikphy.github.io/BezierCurve/
excerpt: Visualizing Bézier Curves
---

Live demo [https://koushikphy.github.io/BezierCurve/](https://koushikphy.github.io/BezierCurve/).

<img src='/assets/images/mics/bezier_screenshot.gif'>  


An example showing [Bézier Curve](https://en.wikipedia.org/wiki/B%C3%A9zier_curve) of any order using [De Casteljau's algorithm](https://en.wikipedia.org/wiki/De_Casteljau%27s_algorithm) of applying recursive [linear interpolation (lerp)](https://en.wikipedia.org/wiki/Linear_interpolation) between a given set of control points. First, a group of linearly interpolating points is calculated between the pairs of consecutive data points. Then, those points are used as new control points to calculate the second set of linearly interpolating points. This method is applied repeatedly until the point tracing the Bézier Curve is obtained. In the code here, all those intermediate interpolating points and lines are shown to understand the method easily. Although the algorithm is computationally expensive for larger use, due to its recursive nature, it is numerically very stable and easy to understand and interpret geometrically. 

This code is inspired by the [SoME1](https://www.3blue1brown.com/blog/some1-results) winning math video ['The Beauty of Bézier Curves'](https://www.youtube.com/watch?v=aVwxzDHniEw) by Freya Holmér.


## Project Link
<a href='https://github.com/Koushikphy/BezierCurve'>https://github.com/Koushikphy/BezierCurve</a>