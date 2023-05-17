---
title: Project 1 URL Shortener
date: 2023/5/04
description: How I spent my time on this project, planning, building, scrapping everything and starting over.
tag: web development
author: Vernon van der Merwe
---
# Project 1 URL Shortener
## All the links to the live apps and repos
---
- [Front End Live app](https://url-shortner-79aa8.web.app)
    - Login: 
        -  email: test@gmail.com
        -  password: Hello123
    - Or just register
---
- [Front End Repository](https://github.com/Vernon-van-der-Merwe/url-shortner)
- [Back End Repository](https://github.com/Vernon-van-der-Merwe/url-parser-serverless-be)
---
- [Front End Commits](https://github.com/Vernon-van-der-Merwe/url-shortner/commits/main)
- [Back End Commits](https://github.com/Vernon-van-der-Merwe/url-parser-serverless-be/commits/main)
---
## Extras
---
- [Blog site your on now - Repo](https://github.com/Vernon-van-der-Merwe/next-portfolio)
- [Blog site Commits](https://github.com/Vernon-van-der-Merwe/next-portfolio/commits/main)
---

# Final Architecture
![image](/images/architecture.png)
# Lets get into it

# Phase 1
## Setup, planning, and what am I getting myself into? 😅
I spent the day setting up my base nextra project (it simplifies this writing and documentation process), Getting it up and running, exploring the documentation and adding some content.

Like so 👇

![image](/images/initialLaningPage.png)

### Wins
- I can document my process now and provide some value to the outside word. Now people can follow the process and learn as-well.

### Shortcomings
- I didn't get to the "actual" project, but I did get to the planning and documentation, which is a good start I guess.
- This documentation project/blog site project, is going to need some work to fit my specific needs, don't know if ill get to it in this test.
- This project needs diagram support, I cant go without diagram support. Already saw a Github thread on it, will explore in the near future.
---

# Phase 2
## Sign off the blog project for now, and setup the 'Short'URL project
Firstly I needed to fix 1 problem, the blog posts aren't being sorted in the way I want them to be sorted, this is definitely going to confuse the readers.
Luckily I found a solution in the nextra docs [here](https://nextra.site/docs/guide/organize-files#default-behavior)

The files are being indexed by the alphabetical filename, not the title in the doc or anything like that, so my temporary solution is to just add the alphabetical prefix to the filename, like so:
- a-thisIsMyFirstBlogPost.md
- b-thisIsMySecondBlogPost.md
- c-thisIsMyThirdBlogPost.md

### Now on to the 'Short'URL project

    - Ill be using React and [Next.js](https://vercel.com/home?utm_source=next-site&utm_medium=footer&utm_campaign=next-website)
    - [MantineUI](https://mantine.dev/) as the UI library
    - [Firebase](https://firebase.google.com/): 
        - for authentication
        - Database and hosting
        - Functions - this is very similar to aws lambda, and azure functions (This changes later on 👀)

1. Let's setup our base.
    - Create a new project on firebase
    ![image](/images/createfire.png)
    ![image](/images/createfire2.png)
    ![image](/images/createfire3.png)
    ![image](/images/createfire4.png)
    - Create the github repo
    ![image](/images/creategh.png)
    - clone the repo
    ![image](/images/creategh2.png)
    - Create my react & next.js project locally
    ![image](/images/creategh3.png)
    - Add mantineUI
        - I installed next.js 13, have only worked with next.js 12 until now... they made changes to the way you structure projects... time to research ...
        - After some research, I found that mantine doesn't support the new way of building next.js 13 apps ...
        - Seems like the only problem is the new [Pages to App](https://nextjs.org/docs/pages/building-your-application/upgrading/app-router-migration) structure, so lets revert that to the old way of doing things.

2. Add our Layout & components.
    - I wanted to a add a component as-well to see if everything is working as expected, so I added a Responsive navbar, and created a dashboard layout.
    ![image](/images/navbar.png)
    ![image](/images/responsiveness.gif)


---

# Phase 3
### Deploy Deploy Deploy 🚀

1. Lets add Firebase and deploy my initial solution.
    ![image](/images/firebaseinit.png)
    - Ran into a problem with payment... need an alternate solution.
    ![image](/images/payment.png)

2. Okay, so had some issues with google payment, but no biggie, seems like vercel offers a similar solution, with a postgres db, serverless functions and edge functions, and then hosting. With a generous free plan :)
    - Deployment was crazy simple, literally just add your repo and they deploy the project for you... done
    - [Blog Site (you are currently on)](https://next-portfolio-plum-six.vercel.app/)
    - [Url Shortener](https://url-shortner-blog.vercel.app/)

3. Now that We have our live site, lets add some serverless functions and persist our some data.
    - I chose this approach of deploying simple projects purely for the fact of keeping things simple to mitigate extra complications when things go wrong in the deployment process.
    - After this I know Ill have a working solution living in the cloud.

4. Okay, after a few hours... I reverted to Firebase... Reasons being...
    - Time is limited, and I don't want to spend time learning a new platform, when I already know firebase.
    - Vercel doesn't have user auth as a service. And I wanted that to have users be able to view their own links.
    - So only problem now is I am stuck with edge functions and not a full node.js backend or even functions...
    - Ill sort that out as soon as it becomes a blocker, I hope i am able to do most of the logic with edge functions... we will see.
    - Made the deployment to firebase

# Phase 4
## ✨ Functionality ✨
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

# Phase 5
## Let get to the Ur UlRedirect functionality, AWS Adventure 🏃🏼‍♂️

What a journey it was to get this working...

The problem we have, is that I would've loved to just stick with firebase functions, but for some reason we cant get the payment to go through. Not my nor my mom nor my dads cards work, and my card is active on another firebase account... so it did work in the past. but whatever...

A very popular option in the react world is vercel, so lets give it a go.
- I deployed one of their functions... but wasn't entirely happy... It wasn't really what I was expecting.

Then I realized I have active functions on my personal portfolio project. That means I can just contact the url shortener DB with the personal portfolio function, through adding a Service account and initializing the firebase admin SDK with that.

After struggling with this for hours, I tried to deploy, and realized that the card problem is blocking my deployment, so they keep the functions active since they have a generous free tier... but they don't allow deployments untill you pay... so I am stuck at square 1.

So I bit the bullet, and decided to deploy a AWS Lambda function, I mean its prefect.
- I can tame mu curiosity of how AWS and lambda func work, since I haven't touched that side of the cloud world.
- I can get a glimpse into a new tech stack.
- and I can access my Firestore DB with the firebase admin SDK and a service account

1. Create an account on AWS
    -   This was simple enough... but I soon realized that I need something called an AIM user, to be able to deploy my function. 
        An AIM user is basically a user that has access to the AWS console, and can do stuff on your behalf.
    - I struggled with trying to create this user and to successfully log into the portal for a good few hours... its not the most straightforward user friendly experience. I still don't think its set up correctly...
        But hey it works.
    - Then I went down the rabbit hole of how I can develop these function apps.
    - I created one on the portal, and opened it online in that editor... its cool and all but I want to develop locally.
    - Then I stumbled across SAM and AWS CLI... I think I struck gold when I found these tools.
        - And I think this is what you were talking about when you sad you guys use IaaS.
        - The AWS Serverless Application Model (SAM) is an open-source framework for building serverless applications. - perfect.
2. Set up the base project
    - This was yet another mission. I spent so much time reading documentation, and ran into so many walls.
        - Auth
        - Very short default timeout, that wasn't as straight forward to figure out
        - Hard to manually add TS
        - The template file is completely new to me...
3. Finally got something deployed... and worked on improving that.
4. Then I had to figure out how service accounts work on firebase since I needed access to the firestore db from the redirect function.
    - Got it working.
    - Get the url 
    - redirect and update the stats like clicks.
    - when err occurs redirect to the error page
5. Added some features: 
    - Added a 500 page to the url project, to redirect to that when the user experiences an issue.
    - Fixed the login and auth routing.

# Phase 6
## Round off, fix some bugs and get this working on the live site.

### Authentication Revamp
Firstly, auth is being wierd so I need to fix that. I need to document the structure off my FE structure to understand the responsibility of the different components and then restructure the auth to make more sense, split the responsibility and make it more reliable.

image of the structure:
![FE Structure](/images/FEArchitectureDrawing.jpeg)


I know this looks messy, but let me explain.

We have a couple of parts:
- Front end (in the front end I know I am bad at naming)
    - This splits in two
    - Pages
        - tsx files
        - the structure creates the routing of the app
    - Components
        - Reusable components
            - tables popups modals etc.
            - Layout & its components
                - Navbar
                - Footer
                - Sidebars
                - but also the layout of the pages
                    - the layout of the Dashboard
                    - the layout of the login and register
        
- Services
    - Where all the logic lives
    - They split into two main categories
        - API Services: These handle the logic of the edge functions, so comminication between the app and the DB and third party API's
        - Page Services: These handle the logic of the pages, so the logic of the components on the pages, state etc. page related stuff. Its primarily to keep the components clean and to keep the logic out of the components.
The last but not least
- Config
    - This is where all the config lives
        - Forms config, firebase config etc.
        - Shared models
        - Context providers, like the auth context provider I created that checks the user auth state changes.

This diagram and research helped me realize how I can improve my auth flow, as well as clean up some functions and then I created a global user context that is basically a combination of my firebase user model and my own firestore user model that I define and store.

### The Vercel EDGE functions dont work...

So to my suprise... the edge functions dont work on firebase, there are workarounds but I dont think its worth it since it requires firebase functions and I am already using aws lambda functions. this is why testing in prod so early is so important. (and reading docs properly 😉)

So my temporary solution is to ... (and while I am typing Github copilot is giving me the right solution 😄)

![FE Structure](/images/ghco.png)

But no, my temporary solution is just to skip the api and route the page service directly to the api's service, so skip the controller/endpoint. This is only possible since both FE and api's are in the same project and also because I am using the same technologies.

The ideal solution would be to add this to the AWS lambda function, or even deploy a new one responsible for the crud operations...

I will do that tomorrow though. Before I go to bed I just want to test the url redirect error handling, since thats the only thing I havent seen working on the live site... lets see...


And it doesnt work... The new auth Context checks whether your auth state has changed, and we need to have that url redirect to be open to the public I assume...

Nope I was wrong, I had a method in the app file that redirected used to the landing page. 
But after reading this (Article)[https://nextjs.org/docs/pages/api-reference/next-config-js/redirects]
I made a redirect that redirects users that land on the base path to dashboard.
This partially fixed my problem, but then when user isn't logged in the auth context throws you to the login page so I had to add a check for the open URL's
Seems like thisll be my next issue, not nice to discover before bed but l;ets hope the propogation of my site might mean its fixed in the morning.

### Its like 4AM, I Cant Sleep, lets fix this.

And it took me literally no time, the site just needed to propagate 😄.

Now if you go on the app, add a url, click shortened version, and the id gets damaged, or url doesnt exist, you get redirected to this page:

![FE Structure](/images/500Page.png)


If you look closely you can even see I pass in a message using query params.

# Phase 7
## Need to finalize and go through the checklist
- [] Site needs a lot of testing, especially the redirect.
- [] Need to add all the api related logic to the Lambda Function.
- [] Setup pipelines for the Lambda Function.
- [] Redirect error page should support error codes as well.
- [] Needs FE validation based on the data, not just generic validation.
- [] Need to ensure all the components follow the same structure.
- [] need a shorter domain for the redirectURl, currently its not really a URL shortener more of a URL elongation app😄
