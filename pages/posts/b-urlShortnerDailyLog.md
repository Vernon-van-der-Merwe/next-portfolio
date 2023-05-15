---
title: Project 1 URL Shortener
date: 2023/5/04s
description: How I spent my time on this project, planning, building, scrapping everyting and starting over.
tag: web development
author: Vernon van der Merwe
---
# Daily log
## All the links to the live apps and repos
- [Repo - FE](https://github.com/Vernon-van-der-Merwe/url-shortner)
- [Live app](url-shortner-79aa8.web.app)
    - Login: 
        -  email: test@gmail.com
        -  password: Hello123
    - Or just register
- [Repo - BE](

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

1. Lets add Firebase and deploy my initial solution.
    - Ran into a problem with payment... need an alternate solution.

2. Okey, so had some issues with google payment, but no biggie, seems like vercel offers a similar solution, with a postgres db, serverless functions and edge functions, and then hosting. With a generious free plan :)
    - Deployment was crazy simple, literally just add your repo and they deploy the project for you... done
    - [Blog Site (you are currently on)](https://next-portfolio-plum-six.vercel.app/)
    - [Url Shortner](https://url-shortner-blog.vercel.app/)

3. Now that We have our live site, lets add some serverless functions and persist our some data.
    - I chose this approach of deploying simple projects purely for the fact of keeping things simple to mitigate extra complications when things go wrong in the deployment process.
    - After this I know Ill have a working solution living in the cloud.

4. Okey, after a few hours... I reverted to Firebase... Reasons being...
    - Time is limited, and I don't want to spend time learning a new platform, when I already know firebase.
    - Vercel doesn't have user auth as a service. And I wanted that to have users be able to view their own links.
    - So only problem now is I am stuck with edge functions and not a full node.js backend or even functions...
    - Ill sort that out as soon as it becomes a blocker, I hope i am able to do most of the logic with edge functions... we will see.
    - Made the deployment to firebase

## Day 4
### ✨ Functionality ✨
Added the Create and read for Urls [commit](https://github.com/Vernon-van-der-Merwe/url-shortner/commit/976ae7079164d6d6bb732ad68d9866d8297116a9)
    - Here I added:
        - Config:
            - Firebase config
        - input:
            - the basic FE create component
            - the basic FE read component/table
        - Logic:
            - the create controller
            - the read controller
            - the url service (and added full CRUD functionality)
            - a basic math function to create our initial short url (DEFINITELY NOT IDEAL, but it works for now)
        - Extras: 
            - Simplified the Navbar
            - Added FE validation for the create component [file](https://github.com/Vernon-van-der-Merwe/url-shortner/blob/976ae7079164d6d6bb732ad68d9866d8297116a9/src/config/forms/config.ts#LL1C17-L1C17)
            - Added notification service for some user feedback [file](https://github.com/Vernon-van-der-Merwe/url-shortner/blob/976ae7079164d6d6bb732ad68d9866d8297116a9/src/services/page/notificationService.tsx#L4)
### Bugs
- Have a bug where reading from the db works on my local but not on the remote app...

## Day 5
### Let get to the UrlRedirect functionality

What an adventure it was to get this working...

The problem we have, is that I would've loved to just stick with firebase functions, but for some reason we cant get the payment to go through. Not my nor my mom nor my dads cards work, and my card is active on another firebase account... so it did work in the past. but whatever...

A very popular option in the react world is vercel, so lets give it a go.
- I deployed one of their functions... but wasn't entirely happy... It wasn't really what I was expecting.

So I bit the bullet, and decided to deploy a AWS Lambda function, I mean its prefect.
- I can tame mu curiosity of how AWS and lambda func work, since I haven't touched that side of the cloud world.
- I can get a glimpse into your tech stack
- Lastly what better way to show you guys what I can do. 😊

1. Create an account on AWS
    -   This was simple enough... but I soon realized that I need something called an AIM user, to be able to deploy my function. 
        An AIM user is basically a user that has access to the AWS console, and can do stuff on your behalf.
    - I struggled with trying to create this user and to successfully log into the portal for a good few hours... its not the most straightforward user friendly experience. I still dont think its set up correnctly...
        But hey it works.
    - Then I went down the rabbit hole of how I can develop these function apps.
    - I created one on the portal, and opened it online in that editor... its cool and all but I want to develop locally.
    - Then I stumbled across SAM and AWS CLI... I think I struck gold when I found these tools.
        - And I think this is what you were talking about when you sad you guys use IaaS.
        - The AWS Serverless Application Model (SAM) is an open-source framework for building serverless applications. - perfect.
2. Set up the base project
    - This was yet another mission. I spent so much time reading documentation, and ran into so many walls.
        - Auth
        - Very  short default timeout
        - Hard to manually add JS
        - The template file is completely new to me...