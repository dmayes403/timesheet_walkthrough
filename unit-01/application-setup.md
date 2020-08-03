# Application Setup

## Objectives

At the end of this unit, you should be able to answer the following questions:

* What CLI command do I use to start a new Angular application?
* What CLI command do I use to include Angular Material in the application?
* How do I start an Angular application?

## Introduction

Angular is a platform and framework for building single-page client applications using HTML and TypeScript. Angular is written in TypeScript. It implements core and optional functionality as a set of TypeScript libraries that you import into your apps.

## Create a new Angular app

```
ng new hr-timesheet
```

When asked if you should include routing, type 'y' for yes and press enter
```
Would you like to add Angular routing? (y/N)
```
When asked what stylesheet format you would like to include, select `SCSS`
```
Which stylesheet format would you like to use? (Use arrow keys)
  CSS 
❯ SCSS   [ https://sass-lang.com/documentation/syntax#scss                ] 
  Sass   [ https://sass-lang.com/documentation/syntax#the-indented-syntax ] 
  Less   [ http://lesscss.org                                             ] 
  Stylus [ http://stylus-lang.com  
```

This will create a directory named hr-timesheet, generate all of the app files and place them in there, and download all of the dependencies specified by Angular CLI. You're free to install more as your project needs them. The above command may take a minute or more, depending on your environment and internet connection speed.

## Create additional folders

Next we will create four additional folders under the `src/app`. The four folders will be called `components`, `interfaces`, `modules`, and `services`.

![Folder Structure](img/folder_structure.png)