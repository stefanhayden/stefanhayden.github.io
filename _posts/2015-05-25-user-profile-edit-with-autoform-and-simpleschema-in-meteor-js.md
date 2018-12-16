---
id: 1750
title: User Profile Edit with Autoform and SimpleSchema in Meteor JS
date: 2015-05-25T00:18:02+00:00
author: Stefan Hayden
layout: post
guid: http://www.stefanhayden.com/blog/?p=1750
permalink: /blog/2015/05/25/user-profile-edit-with-autoform-and-simpleschema-in-meteor-js/
categories:
  - development
---
The steps to creating a form with <a href="https://atmospherejs.com/aldeed/autoform">autoform</a> for editing user profile information are simple but not obvious when trying to tie everything together for the first time.

The first step is the set up the <a href="https://atmospherejs.com/aldeed/simple-schema">Schema</a>. You need to set it correctly for the user data but the profile object is free form where you can add anything you want. Remember that all the things in the profile object are editable by the user. After you craete the schema be sure to attach it to the users collection.

<script src="https://gist.github.com/stefanhayden/565082dd80fea1cd8819.js"></script>

Next you just need to create the form. The autoform quickform helper will spit out a form for all the user data, most of which you probably don't want the user to be editing. Instead we can easily just show the fields we want to let users edit:

<script src="https://gist.github.com/stefanhayden/20fa1f7a56178d5cde55.js"></script>

And that's it. In the autoForm helper the collection accepts either a template helper (no quotes) or a global variable (quotes). For users you need to pass in the "Meteor.users" collection. To set what data to load the doc attribute needs an object with a _id property which the currentUser helper has.