---
title: 3. URL Shortner - Daily log
date: 2023/5/04
description: How I spent my time on this project, planning, building, scrapping everyting and starting over.
tag: web development
author: Vernon van der Merwe
---
# Daily log

## Day 1 : Setup, planning, and what am I getting myself into? 😅
I spent the day setting up my base nextra project (it simplifies this writing and documentation process), Getting it up and running, exploring the documentation and adding some content.

Like so 👇

![image](/images/initialLaningPage.png)

### Wins
- We can document our process now and provide some value to the outside word. Now people can follow the process and learn aswell

### Shortcomings
- I didn't get to the actual "test" project, but I did get to the planning and documentation, which is a good start I guess.
- This documentation project is going to need some work to fit my specific needs, don't know if ill get to it in this test.
- This project needs diagram support, I cant go without diagram support. Already saw a Github thread on it, will explore in the near future.
---

## Day 2
### One small improvement to the blog site
Firstly I needed to fix 1 problem, the blog posts arent being sorted in the way I want them to be sorted, this is definitly going to confuse the readers.
Luckily I found a solution in the nextra docs [here](https://nextra.site/docs/guide/organize-files#default-behavior)

The files are being indexed by the alphabetical filename, not the title in the doc or anything like that, so my temporary solution is to just add the alphabetical prefix to the filename, like so:
- a-thisIsMyFirstBlogPost.md
- b-thisIsMySecondBlogPost.md
- c-thisIsMyThirdBlogPost.md

### Now on to the test project

    - Ill be using React and [Next.js](https://vercel.com/home?utm_source=next-site&utm_medium=footer&utm_campaign=next-website)
    - [MantineUI](https://mantine.dev/) as the UI library
    - [Firebase](https://firebase.google.com/): 
        - for authentication
        - Database and hosting
        - Functions - this is very similar to aws lambda, and azure functions

1. Let's setup our base.
    - Create a new project on firebase
    - Create the github repo
    - clone the repo
    - Create my react & next.js project locally
    - Add mantineUI
        - I installed next.js 13, have only worked with next.js 12 until now... they made changes to the way you structure projects... time to research ...
        - After some research, I found that mantine doesnt support the new way of building next.js 13 apps ...
        - Seems like the only problem is the new [Pages to App](https://nextjs.org/docs/pages/building-your-application/upgrading/app-router-migration) structure, so lets revert that to the old way of doing things.

2. Add our Layout & components.
    - I wanted to a add a component as-well to see if everything is working as expected, so I added a Responsive navbar, and created a dashboard layout.


---

## Day 3
### Deploy the apps, both blog and Url Shortener.

1. Lets add ~~Firebase~~ VERCELL and deploy my initial solutions.
    - ~~Download firebase cli~~
    - ~~I added firebase to my project, and deployed it to firebase hosting.~~

2. Okey, so had some issues with google payment, but no biggie, seems like vercel offers a similar solution, with a postgres db and others. With a generious free plan :)
    - Deployment was crasy simle, literally just add your repo and they deploy the project for you... done
    
