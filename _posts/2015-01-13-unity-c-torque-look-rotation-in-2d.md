---
id: 1738
title: 'Unity C# &#8211; Torque Look Rotation in 2D'
date: 2015-01-13T00:40:52+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1738
permalink: /2015/01/13/unity-c-torque-look-rotation-in-2d/
categories:
  - development
  - unity
---
Getting one object to look at another object in Unity can be a very math intensive project.  In 3D there is an easy way to do this by use the transform to look at another object with a simple call:
<blockquote>Quaternion.LookRotation(target.position - transform.position)</blockquote>
In 2D Unity doesn't hold your hand and you have to figure it out yourself. Most look rotation guides for Unity focus on simply modifying the transform even when talking about moving a Ridgedbody with physics.

If you want to use physics on Ridgedbody to add torque to turn toward another object then the <a href="http://wiki.unity3d.com/index.php/TorqueLookRotation">unifycommunity wiki has a guide for 3D</a>. With slight modifications we can get this same code working for Ridgedbody2D:
<script src="https://gist.github.com/stefanhayden/65a5bf62b29ef160ca76.js"></script>