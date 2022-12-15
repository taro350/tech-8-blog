---
title: 'rclone to Google Drive for my personal images and videos'
status: 'draft'
author:
  name: 'rclone to GD'
  picture: 'https://avatars.githubusercontent.com/u/55218319?v=4'
slug: 'rclone-to-google-drive-for-my-personal-images-and-videos'
description: ''
coverImage: ''
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

### 2\. rclone remote on Google Drive



