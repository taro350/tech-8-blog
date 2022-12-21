---
title: 'rclone to Google Drive for my personal images and videos'
status: 'published'
author:
  name: 'rclone to GD'
  picture: 'https://avatars.githubusercontent.com/u/55218319?v=4'
slug: 'rclone-to-google-drive-for-my-personal-images-and-videos'
description: ''
coverImage: '/images/texturescom_grass0052_2_s-A4ND.jpeg'
publishedAt: '2022-12-15T12:00:13.323Z'
---

As we're reaching to the end of the year, it's time to make more space for yourself and your iPhone!

I haven't uploaded to Google Drive for a long time, and guess what? There are so many videos and images to be uploaded only to save my storage both on my iPhone and mac.

I exclusively created a folder that contains only videos, which is over 400GB. And I tried to start uploading it. The time that will be spent to upload through Firefox browser that Google Drive said was 128 hours. I was just flabbergasted. Am I joking? Yes, sure. While I should've had a Desktop version Google Drive in the first place, if that had been the case, I might've been more encouraged myself to offload my contents on my devices more often, it would still not be sufficient enough for this amount of data. So I need another way to upload this hectic amount of files to upload moderately quickly to Google Drive.

What's the best way to find a solution? Ask Reddit.

> [rclone](https://rclone.org/) is another tool you could try. It's fairly easy to add [google drive](https://rclone.org/drive/), it has you authenticate in the browser. There's also [rclone-browser](https://github.com/kapitainsky/RcloneBrowser) to add a gui.
> 
> Not sure if it would increase the speed, but you could at least fiddle with the transfer threads until you hit whatever maximum google allows.
> 
> I still have some [duplicity](https://duplicity.gitlab.io/duplicity-web/) backups on my google-drive from back when I rented a server and it was faster to package up all the tiny files and send them as 500MB chunks. You say you're in windows though. I wonder if [these alternatives](https://alternativeto.net/software/duplicity/?license=opensource&platform=windows) are any good. It's a different method, can't just copy/paste the files out of goog-drive, so that's something to keep in mind.

("Uploading 1.3TB to Google Drive" on DataHoarder subreddit)

Well I certainly jumped on the same boat and searched for a way to accomplish it. Here's how I did

### 1\. Install rclone

The official [rclone's documentation\] \([https://rclone.org/install/](https://rclone.org/install/)) will help you guide through it. In my case, I just dobrew install rclone

```bash
brew install rclone
```

### 2\. Configure a rclone remote for a client on your project that uses Google Drive API.

Let's get started by typing

```javascript
rclone config
```

rclone asks us:

> e) Edit existing remote
> 
> n) New remote
> 
> d) Delete remote
> 
> r) Rename remote
> 
> c) Copy remote
> 
> s) Set configuration password
> 
> q) Quit config

We want a new remote to Google drive so type "n" and enter.

> Enter name for new remote.

Whatever name you call.

> Option Storage.

At the time where I'm writing right now, 18 is "Google Drive (drive)"

> Option client\_id.

Copy and paste from OAuth Client in your Credentials of API&Services.

> Option secret.

Again, copy&paste it!

> Option scope.

Choose

> 1 / Full access all files, excluding Application Data Folder.
> 
> \ (drive)

And then

> Option service\_account\_file.

Leave it blank as it is.

> Edit advanced config?

No.

> Edit auto config?

No.

Now we have

> Option config\_token.

This is the **most** **important** step because we will authorize our rlone client for Google Drive.

```bash
rclone authorize "drive" "some_hash_generated_by_rclone"
```

Open another tab in your terminal and copy and paste it. rclone automatically open a tab in your browser and you can select, if you have multiple accounts as I do, a Google Account (as a \*tester \*in the perspective of your *external* application), and it tries to authorize it. However, in my case, where I can't be bothered to create an "Organization", I will have to be *a tester* for the \*external \*project I created. So I got an message

> Access blocked: has not completed the Google verification process
> 
> has not completed the Google verification process. The app is currently being tested, and can only be accessed by developer-approved *testers*. If you think you should have access, contact the developer.

Go back your OAuth consent screen in the APIs & Service and search for Test users section and press the "+ADD USERS" button to add one of your Google Account as you are an *tester*, i.e., [whatever@gmail.com](mailto:whaever@gmail.com).

Now try again!

> Google hasn’t verified this app

Ok, it made me feel just insecure just because Google hasn’t verified my app/project. Google is powerful! But anyway just

`Continue`

Next, we're asked from our app/project, "Hey! Our app/project enabled Google Drive API so we want to access it on your Google Account. Can you trust me?"

Sure.

`Continue`

And then rclone prompts

> Success!
> 
> All done. Please go back to rclone.

We now have

> 2022/12/21 10:24:32 NOTICE: Waiting for code…
> 
> 2022/12/21 10:29:25 NOTICE: Got code
> 
> Paste the following into your remote machine --->
> 
> 
> 
> <---End paste

in our terminal.

Copy the `&amp;amp;lt;hash generated by rclone&amp;amp;gt;` and paste in

> config\_token>

We're almost there.

> Configure this as a Shared Drive (Team Drive)?

No.

> Configuration complete.

Yeah!! We did it!

### 3\. Let's use "rclone copy" to copy your images to Google Drive!

```javascript
rclone ls <your remote>:/<dir>/<sub_dir>
```

To list the contents of the a directory or subdirectoy .

### 4\. It's time to "copy" your folders/images to Drive!

Take a look on your Google Drive to see whether that's working correctly. If it is, is rclone cool, isn't it?

That's it! Have a great day!



