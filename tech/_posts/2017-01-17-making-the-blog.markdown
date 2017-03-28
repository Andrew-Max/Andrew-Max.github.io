---
layout: post
title:  "Make a Photo Blog with Jekyll, Github Pages, and AWS S3"
date:   2017-01-12 15:39:40
s3-base: https://dmw492fxu64ad.cloudfront.net/blog-how-to
---

In this post I'll go through all the libraries and dependencies required to create a similiar blog, how to install them, and how I setup the content of the blog itself

# Dependencies: What you need to create a similiar blog

## Git and a Github Account">
All the code for this blog is open source on github. Check it out at <a href="https://github.com/Andrew-Max/Andrew-Max.github.io">https://github.com/Andrew-Max/Andrew-Max.github.io</a>

Disclaimer: The ideal intended audience for this blog is everyone. My goal is to make it so you could try to repeat these steps with no technical knowledge. Unfortunately there is no way to write it without assuming the baseline of knowing git and running some basic command line commandes.If you don't already have these skills, I encourage you to check out codeschool.com which has some good free resources for learning these things. If you can't follow something, reach out to me and let me know!

# Basic Rundown

Right now I'm traveling South America and I wanted to make a blog to document my trip. I didn't feel like learning wordpress and I don't like the fact that wordpress hides your code from you. Outside of wordpress, it seems like Jekyll is the easiest platform to create your own blog, and that's what I used here. Jekyll is written in Ruby, and feels fairly similar to writing Ruby on Rails code.

One of the big advantages of using Jekyll is that it has a github integration that allows you to serve the blog just by hosting it on github. That means no configuring or managing webservers and you don't even need a domain name. All I do to deploy my code is to push to the master branch of the related repo and the content at `andrew-max.github.io/` gets updated almost instantaneously.

One of the nice things that Wordpress gives you that Jekyll doesn't is dealing with creating image assets and hosting them but it's nearly free(cents per month) and pretty simple to do this yourslef on Amazon's `s3` cloud storage tool.

In this post I'll go through all the libraries and dependencies required to create a similiar blog, how to install them, and how I setup the content of the blog itself

# Dependencies: What you need to create a similiar blog

## Git and a Github Account

Github plays a crucial role in this setup, becuase they are doing all the work of serving the code for free just by pushing my code to github. <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git">There is a good guide for installing Git</a> and <a href="https://www.codecademy.com/learn/learn-git">some good free tutorials for learning it.</a>

[You can sign up for github here: https://github.com/join ](https://github.com/join)

## Ruby, Gems, and Jekyll

This blog is built on Jekyll blogging library and parser which is in turn built on Ruby, and Ruby Gems. I recommend using <a href="https://rvm.io/">RVM</a> to install ruby and gems if you don't aleady have it. Use the <a href="https://rvm.io/rvm/install">RVM Installation Guide</a> to get started. The jekyll website also has a good guide for getting these installed at <a href="https://jekyllrb.com/docs/installation/">https://jekyllrb.com/docs/installation/</a>

## An Amazon AWS account

This blog is photo heavy and relies on a cheap and reliable way to store and serve the photos. Amazon's s3 is perfect for this. <a href="https://www.amazon.com/ap/signin?openid.assoc_handle=aws&opnid.return_to=https%3A%2F%2Fsignin.aws.amazon.com%2Foauth%3Fresponse_type%3Dcode%26client_id%3Darn%253Aaws%253Aiam%253A%253A015428540659%253Auser%252Fawssignupportal%26redirect_uri%3Dhttps%253A%252F%252Fportal.aws.amazon.com%252Fbilling%252Fsignup%253Fredirect_url%253Dhttps%25253A%25252F%25252Faws.amazon.com%25252Fregistration-confirmation%2526state%253DhashArgs%252523%2526isauthcode%253Dtrue%26noAuthCookie%3Dtrue&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&action=&disableCorpSignUp=&clientContex1t=&marketPlaceId=&poolName=&authCookies=&pageId=aws.ssop&siteState=pre-register%2Cen_US&accountStatusPolicy=P1&sso=&openid.pape.preferred_auth_policies=MultifactorPhysical&openid.pape.max_auth_age=120&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&server=%2Fap%2Fsignin%3Fie%3DUTF8&accountPoolAlias=&forceMobileApp=0&language=en_US&forceMobileLayout=0">You can sign up for an aws account here</a>

## And possibly a unix based machine(Mac or Linux)

I would almost guarantee that everything I'm doing here could be done on Windows but I'm not sure what the differences would be and it may be more difficult. This blog assumes you are using mac or windows.

# Installing and Running the app

## Clone the andes-photocentric-jekyll-theme repo, bundle

Assuming you have a git, go to your command line and run: `$ git clone https://github.com/Andrew-Max/andes-photocentric-jekyll-theme.git`. This will copy the code for the blog to your local machine.

## Install the `bundler` gem and bundle the repos dependencies
Enter that directory with the `cd` command

now run `$ gem install bundler`. Then install all the app's dependencies but simply enetering `$ bundle`.

Note, the `$` commands is shorthand for telling you that this is a command line command. So if I say `$ gem install bundler` you only actually type "gem install bundler"

## Run the App
Now just run `$ jekyll serve` to run the app. It should be available in the browser by typing `localhost:4000` into the url bar

If this doesn't work your next steps are the same as all other trouble shooting. Read the error message(yeah, like really, read it a couple times. Think about what it means), try to fix it, and then look it up on google. If that doesn't fix it, get some coffee and then do it again.

# Creating Content

If you've gotten this far, you are half way there and already have a running application, but all you've got is an empty blog with a simple sample post. Let's fix that!

## Creating a new post
To create a new post, add a new file to the `_posts` directory with a title in the format
`YEAR-MONTH-DAY-title.MARKUP`
for example `2012-09-12-how-to-write-a-blog.md`

### Inside the new post file
There are two major parts to a post: front-matter and content

#### Front matter
Front matter is metadata that is required by Jekyll and this theme to compose the blog.

It should be at the very top of each blog post in the format:
```
---
layout: post - literally the word `post`
title:  make a title
date:   date from the file name
s3-base: url of the bucket of your photos  for example
preview: location of a photo in the bucket at s3-base
previousurl: you can link to the previous article here
nexturl: you can link to the next article here
images:
  - type: horizontal
    id: 1
  - type: vertical
    id: 1
  - type: pano
    id: 1
---
```
Note that the front matter must start and end with ```.

All the data necessary to generate the photo wall is in the front matter: a layout type of post, the correct image bucket configuration and the images. You can change the order of the images to change the order they display in and improve the photo wall layout. We'll go over exactly what values to give to the s3-base and images and how to set that up later on.

Check out the sample post in `_posts` for a working example of what all of this looks like

## Prepping photos locally
To make a photo blog, first you need some photos. Pick a few photos that you want to be on the wall of your first post and set them aside somewhere.

Becuase this relies on a very specific directory structure for your hosted photos, it's almost necessary to replicate that structure locally before uploading and I've created some scripts to help you set this up.

In the _scripts folder I have included two scripts which help automate prepping the photos.

The first step is to create the directory where you want to hold your photos locally, go there, and run`$ bash <base git directory>/scripts/init_blog_post_structure.sh`. This will create the directories you need. Note you need to replace <base git directory> with wherevery you cloned your repo to so it can find the script.

Next, fill this directory with the photos you set aside (landscapes in the horizontal, portraits in vertical, panos in pano) and run the `$ bash <base git directory>/scripts/setup_blog_pics.sh` script. This will resize and redistribute your photos to the proper directories and make sure they have the proper names.

## Getting the photos on s3
Once you have your directory of organized, named, and sized photos, the last step is to upload them on Amazon's s3 file storage tool. This part is a bit tricky so make sure to follow the instructions carefully!

### Creating your blog's main bucket
Assuming you have created an AWS account, the next step is to find the s3 console and create a bucket.

On the AWS console main screen, you can find "s3" under the "Storage" section. Once you are in there, hit the "create new bucket" button. Give your bucket a unique and easy to remember name connected by dashes (mine is "amax-photo-blog") and set your region to any "US East" or "US West option" (if you, are in another country, pick whatever is closest to you or wherever you think your target audience is most likely to be.)

Click next at the bottom and then click next at the bottom again to skip the Set Properties page. On the third setup page entitle Set Permissions, open Manage Public Permissions and click the checkbox for "everyone" to get "read" permissions for the "objects" column. With out doing this, only you will be able to see your photos and they won't display on your blog.

Click "next" at the bottom again and then "create bucket" and you should finally have your bucket

## Create s3 sub directories and add photos to them
Almost there. The last step is to actually upload your photos that your prepared in the "Prepping photos locally". It's imporant to be extremely careful here, becuase your blog depends on these photos being at the exact right location and any naming error will make it so your blog can't find them.

You can think of s3 exactly like directories on your regular computer, with the exception that it gives every file a publicly available url. You can create named directories(folders), create named directories in those directories, and add files. The file will then be available at the location you just created with some extra pieces in front of the url.

If you recall from above I said the s3 directory structure should be:
lvl 1: At the top is the main bucket,


lvl 2:  Under the main bucket is one directory for each blog post, named however you want,

under each lvl 2 directory, you need 2 level 3 directories:

lvl 3 `full` - the large photos that get displayed when you click on a photo

lvl 3 `thumb` - the thumbs that get displayed on the photo wall

also at this level should be an image called `cover.jpg` which will be the preview image for this album

In each of the level three directories, there should be three subdirectories:

lvl 4 : `horizontal`

lvl 4 : `vertical`

lvl 4 : `pano`

lvl 5 : Inside of these directories should be numbered photos starting at 1 ie `1.jpg`. So in the images section

For example, some of my s3 directories are

lvl 1          | lvl 2 |lvl 3|  lvl 4   | lvl 5
amax-blog-posts/quito/thumb/horizontal/1.jpg
amax-blog-posts/mompiche/full/pano/3.jpg
amax-blog-posts/italy/full/vertical/27.jpg

### Tying your blog post to your s3 images

Once you have the s3 images all setup. The last step is to make sure the front-matter in your blog post file(that's the part at the way top between the `---` marks)has the right data for the s3 bucket so it know how to link to the photo's there

The front matter looks like:
```
---
layout: post - literally the word `post`
title:  make a title
date:   date from the file name
s3-base: url of the bucket of your photos  for example
preview: location of a photo in the bucket at s3-base
previousurl: you can link to the previous article here
nexturl: you can link to the next article here
images:
  - type: horizontal
    id: 1
  - type: vertical
    id: 1
  - type: pano
    id: 1
---
```
The important pieces here are: `s3-base`, and the content of the `images section`
The s3 base should be the whole link to your s3 bucket plus the name of the top level directory for that post

an example of this is
`https://s3.us-east-2.amazonaws.com/amax-blog-photos/medellin/`

or

`https://s3.us-east-2.amazonaws.com/amax-blog-photos/costa-rica/`

This piece is telling the post where all the photos for that post are located

The images section is where you manually list out all of the photos that you want to be on your photo wall

Let's take for example
```
---
images:
  - type: horizontal
    id: 1
---
```

This is essentially saying, at the `s3-base` there is both `full` and `thumb` directories, in both of those is a horizontal directory, and there will be a photo `1.jpg`

these match up with the directories we just made in s3 which would be

`<s3-base>/<blog-post-title>/full/horizontal/1.jpg` (the photo that gets displayed when you click on a photo wall photo)

and

`<s3-base>/<blog-post-title>/thumb/horizontal/1.jpg` (the photo that gets displayed on the photo wall)

note that in s3, you can click through the directories and find a photo and if you click on that photo it will tell you the full link to that photo.

Now go organize some photos and make some posts!

## Deploying your Blog

In the realm of web apps, the word deploy means to take something you have made on you computer, and to put it on a web server so other people can access it. The blog you made only lives on your local computer now and what's the point of that? We need to deploy it.

To do this we are going to use git and github.

### Setup a github repo with the exact same name as your user account + github.io

Github has a trick where if you put a jekyll app in a repo named exactly `<your-github-account-name>.github.io` it will serve that app at `https://<your-github-account-name>.github.io`

so for example, my git-hub name is `andrew-max` (I'm boring, I know), so I created a repo named `andrew-max.github.io` and my blog magically get's served at `https://andrew-max.github.io`

### create your repo

Login to your github.com account. Once you are logged in, click the plus sign in the top right hand corner and select "New Repository" and give the repo the name as instructed above (<your-github-account-name>.github.io) and click the green "Create Repository" button

### Push your blog code to your repo
Time for some git magic. Go back to your command line and find the directory you cloned earlier. Right now that directory is tied by git to my `andes-photocentric-jekyll-theme` repo on my account. Now you want it tied to <your-github-account-name>.github.io`

For this we need to change the `remote` value of your repo which tells it which remote repos to connect to

to look at all of your `remotes` enter `$ git remote -v`

We want to switch the one called `origin` to be tied to your repo not mine. For this you can type `$ git remote remove origin`. Now your local repo is not tied to any remote so we can add the new remote repo to it.

First go to the github page for the repo you just created and find the green 'clone or download' button on the right hand side of the page and click it. This should open up a little window, unless you already know how to use SSH make sure it says "Clone with HTTPS". If it says "Clone with SSH", find the button to switch it to HTTPS and copy the link.

Now back at your command line enter

`$ git add .` (only if you have made some changes)<br>
`$ git commit -m "first commit"` (only if you have made some changes)<br>
`$ git remote add origin <url-you-just-copied>`<br>
`$ git push -f origin master` (WARNING: the -f means force and it's generally a bad idea, but in this case it's okay) and if you refresh your repo page on github, your code should all be there.

## LAST STEP! Make sure the repo is setup to serve your blog

This should happen by default, but just to make sure, find the "Settings" link on the main page of your repo, click it, and go near the bottom of that page to where it says "Github Pages" If it has the green checkmark which says "Your site is published" click the link and it should take you to your new blog on the public internet! If not give it a couple minutes and make sure that your code push worked.

## You have a live photo blog!

From here, any new changes you make, just commit them and push them to github and your website should automatically redeploy within a few minutes.

If you end up publishing a blog with my theme, let me know! I'd love to see it!