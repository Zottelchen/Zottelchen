## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="30"/> Forbidden Fruit - A Neural Network Experiment

<img title="" src="https://raw.githubusercontent.com/Zottelchen/Zottelchen/main/img/forbidden_learning.png" alt="" width="328">

**Goals:**

* Learn about Neural Networks.
* Develop a game where you answer questions by holding the objects (fruits) into the camera.
* Be at least a little creative about hints. 

**Tech:**

* yolov5 - The model was trained from scratch,
* PySimpleGui - Just check it out, it is pretty neat to create a GUI quickly.

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="30"/> Edge Detector 2000 - A Comparison of Edge Detection Algorithms

<img src="https://raw.githubusercontent.com/Zottelchen/Zottelchen/main/img/kantendetektor.png" title="" alt="" width="268">

**Goal:**

* Compare the speed of multiple edge detection algorithms of multiple libraries.
* Print a simple graph for comparison.

**Tech:**

* PySimpleGui - This is reoccurring because I like it. Also, most professors are overjoyed if they get to see a proper UI once in a while.
* OpenCV, scikit-image - The Canny/Sobel/Laplace Edge Detection algorithms were compared.
* SciPy - A very basic implementation of the Canny algorithm was written with it. It was painfully slow.
* Matplotlib - We wanted a simple graph, we got a simple graph. Graphs for everyone.

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="30"/> [map.drehmal.cyou](https://map.drehmal.cyou/) - A Map for a Minecraft World

*No picture here, look at it online!*

**Goal:**

* Creating a map for the fantastic community Map Drehmal - if you like Minecraft, you should check it out!
* The map should not only include the fantastically created landscape, but should contain every information that a player might need. It should include every chest with every item, should show every monster location etc.
* High traffic is expected, but I don't want to spend a lot of money on this, so hosting this as cheap as possible is another goal.

**Tech:**

* Minecraft Overviewer - Thankfully, I did not have to write the rendering part for the maps. I "only" had to write the filters. That means a lot of digging in the Minecraft file structures, finding where items are saved  in chests, barrels, item frames, armor stands, lecterns, ... Then read stuff like item IDs, names, enchantments, etc. Similar things for horses. Then get some textures and translate some internal stuff.
* Hetzner Cloud Servers - The rendering at this detail level takes about 2-3 days. Hooray for powerful servers you can rent by the hour! (Minecraft Overviewer only renders on the CPU.)
* Backblaze B2 - Most of the image assets are here. 56.678 folders. 225.631 files. 16,9 GB.
* Netlify - This one hosts the actual HTML files and redirects to...
* Cloudflare - Thanks to the Bandwidth Alliance between Backblaze & Cloudflare, B2 egress costs nothing (operational costs are still there, but they are cheap by comparison). Cloudflare proxies everything and handles a lot of traffic really well (2 TB+ at its peak).

**Note:**

* This was before Cloudflare Pages and Cloudflare R2 existed. These things might be worth to look at for the next update/iteration of this map.

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="30"/> POIGen - A temporary(?) workaround for map generation

*Once again no picture, but this time because it is a console application. However, you can check it out at <https://github.com/Zottelchen/poigen>!*

**Goal:**

* A moderator/builder of the Drehmal project asked why my filters didn't work for newer versions of the map. So, I checked out Minecraft Overviewer and found that Minecraft changed its world format slightly in update 1.17. Entities are now saved in an extra folder. At least some of them are. Chests and some other block entities are still saved in the same location as before. The original goal was to fix my filters, the new goal was to fix Minecraft Overviewer. Which I didn't do thanks to some time constraints (Did someone say exams? \*shudder*).

**Tech:**

* Instead, I wrote my on little tool. Which generates the JSON files required for markers to show on the map.
* Thanks to already existing (well-enough working) NBT libraries (and reusing a lot of old filter code), this was way faster than figuring out Minecraft Overviewers inner workings.

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="30"/><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg" width="30"/><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" width="30"/> ESO Soundboard

<img src="https://raw.githubusercontent.com/Zottelchen/Zottelchen/main/img/eso_soundboard.png" title="" alt="" width="419">

**Goals:**

* Building a Soundboard including all dialogue files of Elder Scrolls Online. At that time (U31), that meant 195.479 audio files.
* Honestly, there was no good reason to do this except to see if I can.

**Tech:**

* EsoExtractData/FFmpeg - Luckily, there is already a pretty good data mining tool for ESO. It even offers to convert the audio files into OGG. Sadly, something is off about these OGG files. So, let's use FFmpeg to convert OGG to OGG. Now it works. ✨Magic✨
* Python -  Sadly, there was no direct link between those audio files and the corresponding subtitles from the language file. Because I don't want to label that many files by hand, I decided to use voice recognition (vosk). And then I fuzzymatched whatever was detected with strings from the language file. It worked surprisingly well.
* Hetzner Cloud Servers - Once again, great for running projects for a couple of days. On day 2 I've realized, I should have added some sort of checkpoint into my script. Or used a small database. Oh, well, it finished after 10 days, spitting out a single 100 MB JSON file. It was not as fast as it could have been, but the script was like 20 lines, and I was not in a rush.
* Cloudflare Pages / B2 - Instead of working with redirects to a public bucket on B2 Cloudflare, this version uses a worker to fetch the content from a private bucket. (R2 did not exist at this point.)
* HTML/JavaScript - I wrote a small web client to search through the "database", download and play the audio files. But for obvious reasons not public. This thing is completely static (except for the B2-fetching), there is no database which smartly queries. There is you and your PC and there is a pruned 14 MB JSON file. It is not the pinnacle of performance, but it works.

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/godot/godot-original.svg" width="30"/> Moneyshot Arcade

<img src="https://raw.githubusercontent.com/Zottelchen/Zottelchen/main/img/arcade1.jpg" title="" alt="" width="640">

**Goal:**

* Create a fun little game which contains other little games.

**Tech:**

* Godot - I have a heart for open-source software, and this game engine is fantastic.
* Tiled - At that point, the Godot level editor wasn't great, especially when working with multiple layers. It has improved a lot since  then, though!
* Aseprite - I have learned, that I am not great at drawing stuff, but you have to agree, this is fine art and should be shown in the museum of modern arts:
  
<img title="" src="https://raw.githubusercontent.com/Zottelchen/Zottelchen/main/img/arcade2.png" alt="" data-align="center" width="608">

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/godot/godot-original.svg" width="30"/> Lucid

<img src="https://raw.githubusercontent.com/Zottelchen/Zottelchen/main/img/lucid.png" title="" alt="" width="634">

**Goal:**

* A simple metroidvania-like game.

**Tech:**

* Godot - I worked a lot on the AnimationTree and Hitboxes in this one. AnimationTrees and I are in a love-hate-relationship.

___

## <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original.svg" width="30"/> Self-hosting stuff

*Sorry, no images either. But if you are curious which server I crashed today, feel free to take a look at my status page: <https://status.gpu.cx>*

**Goals:**

* Reduce the impact of global surveillance companies on my private life.
* Pay as little money as possible.
* Play with cool software.
* Learn how to fuck up and restore databases.
* Add "just 1 more" thing.

**Tech:**

* Generally: Docker, Docker-Compose & a (dockerized) Caddy Server. Backups are done with Kopia and Updates with Watchtower. Monitoring with Uptime-Kuma & Healthchecks.io (for cron jobs).
* Domains are usually bought at Porkbun and managed with Cloudflare. Thanks to the API Caddy can do the TXT-Challenge and Cloudflare can still be the MITM. (Yeah, I know.)
* I love RSS. I hate "social networks" or "news" who don't provide full-text RSS. I *will* try to build my own RSS feeds if none are provided.

**Plans:**

* Better monitoring with Grafana, Prometheus & Loki. Netdata does not feel right.

* Kubernetes.

* Get rid of Cloudflare at some point.
