# 2021-02-23 Introduction to Containers

Welcome to The Workshop Collaborative Document 
 

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents. 

All content is publicly available under the Creative Commons Attribution License 

https://creativecommons.org/licenses/by/4.0/ 

 ---------------------------------------------------------------------------- 

## 👮Code of Conduct 

* Participants are expected to follow those guidelines: 
* Use welcoming and inclusive language 
* Be respectful of different viewpoints and experiences 
* Gracefully accept constructive criticism 
* Focus on what is best for the community 
* Show courtesy and respect towards other community members 
 

## ⚖️ License 

All content is publicly available under the Creative Commons Attribution License: https://creativecommons.org/licenses/by/4.0/ 

 

## 🙋Getting help 
to ask a question, type `/hand` in the chat window 

to get help, type `/help` in the chat window 

you can ask questions in the document or chat window and helpers will try to help you 
 

## 🖥 Workshop website 

[Workshop website](https://escience-academy.github.io/2021-03-23-containers/) 


🛠 Setup 
[link] 

Download files
[link]
 

## 👩‍🏫👩‍💻🎓 Instructors 

Johan Hidding, Mateusz Kuzak 
 

## 🧑‍🙋 Helpers 

Jens Wehner, Carlos Martinez Ortiz 
 

## 👩‍💻👩‍💼👨‍🔬🧑‍🔬🧑‍🚀🧙‍♂️🔧 Roll Call 
Name/ pronouns (optional) / job, role / social media (twitter, github, ...) / background or interests (optional) / city 

    *data removed*

## 🗓️ Agenda 

| Time | What |
| ---- | ---- |
| 09:00-09:30 | Welcome and Icebreaker |
| 09:30-09:50 | Introducing Containers |
| 09:50-10:00 | *... Coffee break* |
| 10:00-10:30 | Introducing Docker |
| 10:30-10:50 | Exploring and Running Containers |
| 10:50-11:00 | *... Tea break* |
| 11:00-11:20 | Docker Hub |
| 11:20-11:30 | Cleaning up Containers |
| 11:30-12:00 | Your first own Container images |
| 12:00-13:00 | *... Lunch Break* |
| 13:00-13:50 | More complex Container images |
| 13:50-14:00 | *... Lemonade break* |
| 14:00-14:15 | Containers in the Cloud |
| 14:15-14:30 | Building Websites using Containers |
| 14:30-14:45 | Containers in Research: Reproducibility |
| 14:45-15:00 | Post-workshop survey and evaluation |

## 🧠 Collaborative Notes 

### Icebreaker
What is the habit you picked up during corona lockdown that you like and would like to keep after we can leave our homes again?

    *data removed*
    
## Introducing Containers

## Exercise 1.
### Part 1 (5 min) What’s Your Experience? 

Take a minute to think about challenges that you have experienced in using scientific software (or software in general!) for your research. Then, share with your group and try to come up with a list of common gripes or challenges. 

Write down here. 

Group 1:
* dependency issues with libraries (e.g., Perl, Python, ...)
* unclear documentation / setting everything up, getting everything up and running
* certain software only available for certain OSs
* separating different parts of the pipeline so they do not start to conflict with each other
* backwards (in)compatibility

Group 2:
* exisiting containers with R-packages inside. So cannot "install" new ones.
* version control with coding packages
* new to coding/programming and will have possible problems in future that I want to prevent when I encounter them.
* introducing others to containers and migrate for others to reproduce (like filepaths and other similar problems that change with sharing with others)

Group 3: 
* Compiling is terrible (especially with no documentation), 
* environment variables, 
* versions changing, 
* back-compatibility and dependencies, 
* data not available

Group 4: 
* Reproducibility, maintaining older software
* Managing software package installation/dependencies, version control
* Liscenced software can be a problem with many collaborators 
* Managing the size of installed libraries 
* Manual building of libraries is very time consuming


Group 5: Reproducibility, Documentation, Dependencies. Having something working independent of the platform.
* Easily deploy someone else code.
* Managing dependencies for organizing and sharing data.
* Standardise analysis pipelines.
* Saving time in implementing others code.


Group 6: Dependencies nightmares of software versions. Take over someone else's software can be hard, understanding other person's software. Documentation is not always present or good enough.

### Part 2 Exercise (5 min) Software and Science 

Again, take a minute to think about how the software challenges we’ve discussed could impact (or have impacted!) the quality of your work. Share your thoughts with your group. What can go wrong if our software doesn’t work? 

Write down here:

Group 1:
* wasting lots of time trying to fix issues/problems (that could have been avoided if one had set things up in a different/better way from the beginning)
* software hoping if a particular pieces of software doesn't work
* cannot guarantee that others will be able to reproduce results (if things are not packaged up in a way that guarantees reproducibility)

Group 2:
* existing tool, but difficult for others to install
* takes a lot of time to solve these kind of issues (technical), instead of the program itself
* everyone has "multiple versions of the truth" on their own computers

Group 3: 
* Time consuming,
* finding suboptimal alternatives, 
* errors due to lack of documentation, 
* mental health issues

Group 4: 
* It can be frustrating when research software doesn't work out of the box
* Managing software collectively can be very time consuming when people use different platforms/setups.
* It can lower the impact of your work (software) if it is not easily deployable
* If the software doesn't work as described this negatively impacts the reproducability of your work.


Group 5: 
*  Rerunning other peoples' code can cost you a lot of time. 
*  Different outcomes of same algorithms (what is supposed to be the same). 
*  Readability and reproducibility makes it easier to detect flaws in the code. 
*  Collaborating across OS distributions.

Group 6: Time: it takes longer to understand code or to make it work, software will be less attracktive to peers if it's difficult to take over or hard to understand. If you can get it to run, it may be through a hack because of the lack of understanding. What can go wrong? Building on someone else's software can go wrong if you don't completely understand the software underlying your work. Reproducibility can be a problem if the software or configuration is not understood. Not reusing software may make you reinvent the wheel.

### Break start again 10:02

☕

### Introducing Docker
* Q: Using a virtual environment can solve “python version” issues, but there is no extra OS. So is containers always the best solution?
* A: If a Python application interact with other components or it depends of an specific file structure. A virtual environment won't be enough.

List our running containers:
```
$ docker containers ls
```

Running hello world:
```
$ docker run hello-world
```

### Exercise 3. (3 min) Run the Alpine Docker container 

Try downloading and running the “alpine” Docker container. You can do it in two steps, or one. What are they? 

Done? 
* Yes!
* running "docker run alpine" doesn't seem to do anything (after "docker pull alpine") -- correct ;-)
* Done

```
$ docker run alpine
```

'Alpine' doesn't run any command, but we can tell it which command to run: `docker run alpine <COMMAND>`, for example:
docker run alpine echo Hello-World!
```
$ docker run alpine cat /etc/os-release
```

### Exercise 4 (3 min) Hello World, Part 2
Can you run the alpine container and make it print a “hello world” message? 

* Yes
* Done
* yes, after several tries ;) (can you do everything "bash" after docker run alpine?)

Solution:
```
docker run alpine echo "Hello World!"
```

### Interactive containers
You can run an interactive container by adding `-it` option

```
$ docker run -it alpine sh
```

Type linux commands inside the container. Exit the container by typing `exit`

### Exercise 5. (3 min) Practice 

Can you find out the version of Linux installed on the “busybox” container? Can you find the busybox program? What does it do? (Hint: passing --help to almost any command will give you more information.)


```
$ docker run busybox /bin/busybox --help
```
longer version:
```
$ docker pull busybox
$ docker run -it busybox sh
$ / # busybox --help
BusyBox v1.32.1 (2021-03-09 19:16:02 UTC) multi-call binary.
(...)
	BusyBox is a multi-call binary that combines many common Unix
	utilities into a single executable.  Most people will create a
	link to busybox for each function they wish to use and BusyBox
	will act like whatever it was invoked as.
(...)
```
```
cat /proc/version 
```
This still gives you information about the host and not about the container operation system.

## Exercise (4 min) What container is right for you? 
Find a Docker container that’s relevant to you. If you’re unsuccessful in your search, or don’t know what to look for, you can use the R or Python containers we’ve already seen. 

Once you find a container, use the skills from the previous episode to download the image and explore it.

Questions (about the exercise):
* Are non-official images also good to use? (Do you need to check for maintenance or something?)
    - you should trust the source of the image, otherwise there may be security implications
* if you need an account (login) how to do this in the terminal? so that you can pull them?
    - you do not need an account for pulling a container.
* I get an access denied error for some containers, how to solve that?

Answers:
- [Thredds](https://hub.docker.com/r/unidata/thredds-docker), a file server for NetCDF
- Wolfgang: [rocker/r-base](https://hub.docker.com/r/rocker/r-base)
- same as Wolfgang
- Vantage6: https://hub.docker.com/r/s102099/vantage6-node
- Rodrigo [biocontainers/fastqc](https://hub.docker.com/r/biocontainers/fastqc): Error response from daemon: manifest for biocontainers/fastqc:latest not found: manifest unknown -- works if I provide a specific tag, e.g. `docker pull biocontainers/fastqc:v0.11.9_cv8`
- Fini: [shinyproxy-demo](https://hub.docker.com/r/openanalytics/shinyproxy-demo) "pull access denied for shinyproxy-demo, repository does not exist or may require 'docker login': denied: requested access to the resource is denied" :(. It has the most downloads. Maybe make your own with just r-base? [r-base](https://hub.docker.com/_/r-base)
- Felicia [rocker/tidyverse](https://hub.docker.com/r/rocker/tidyverse)
- Christine [Django or Flask]: Django is deprecated, Flask has no verified maintainer :(
- Casper: [contnuumio/miniconda3](https://hub.docker.com/r/continuumio/miniconda3)
- Caspar: haskell (Johan: +1)
- Lisa: mmbumcu/bactofidia
- Nathan: [pandoc/core](https://hub.docker.com/r/pandoc/core) and [pandoc/latex](https://hub.docker.com/r/pandoc/alpine-latex): for creating PDFs without directly scripting with LaTeX
- Nele: rasa, rasa x


## Exercise (3 min) What is in the name? 
How would I download the Docker container produced by the rocker group that has version 3.6.1 of R and the tidyverse installed? 

Answers:
- `docker pull rocker/tidyverse:3.6.1`

Working in alpine docker:
* `docker run -it alpine sh`
* `apk add --update python3 py3-pip python3-dev `
* `python3 --version`
* #install packages for python
* `pip install cython`

## Exercise (4 min) Searching for Help 

Can you find instructions for installing R on Alpine Linux? Do they work? 

Answers:  
- `apk add R`  
- `apk add R R-dev R-doc`


### Exercise: Take a Guess

Do you have any ideas about what we should use to fill in the sample Dockerfile to replicate the installation we did above?



## 🥗🍛 Lunch Break untill 1 pm CET !!!

Dockerfile looks like this:

```
FROM alpine
...
CMD ["python3"]
```

```
FROM alpine:3.13
RUN apk add --update python3 py3-pip python3-dev 
RUN pip install cython
RUN apk add R
CMD ["sh"]
```
#then run
* `docker build --tag python-docker .`

### Exercise (10 min): Review! 

Think back to earlier. What command can you run to check if your image was created successfully? (Hint: what command shows the images on your computer?) 

We didn’t specify a tag for our image name. What did Docker automatically use? 

What command will run the container you’ve created? What should happen by default if you run the container? Can you make it do something different, like print “hello world”? 


### docker tag question
Finding out the version begind 'latest' (or any other) tag
docker image inspect --format '{{json .}}' "$IMAGE_ID" | jq -r '. | {Id: .Id, Digest: .Digest, RepoDigests: .RepoDigests, Labels: .Config.Labels}'
https://ryandaniels.ca/blog/find-version-tag-latest-docker-image/

### Building a docker image
Notice the dot (.) at the end of the line -- this means 'my Docker file is in my current working directory'
```
$ docker build -t alpine-python .
```

run the image:

```
$ docker run -it alpine-python
```

### Using Github Pages

Edit your README.md:

```
# readme-pages
Example for generating Github.io pages from Readme with Pandoc.
```

Running pandoc container:
```
$ docker run pandoc/core --version
$ mkdir build
$ docker run -v ${PWD}:/tmp pandoc/core /tmp/README.md --standalone --output=/tmp/build/index.html
```

On windows you most likely have to use the powershell and one of the following commands will work:
```
docker run –v %cd%:/tmp/ pandoc/core  /tmp/README.md
docker run –v C:\\Users://tmp pandoc/core /tmp/README.md
```

Now we can see out file was built:
```
$ ls build/
$ cat build/index.html
```

### 🍋 🍹 Break start again 14:00

Go to Github, create an action (this github action file should be in a folder in your github repositorty: `.github/workflows/main.yml`):

```
name: Deploy pages
on:
    push:
        branches:
          - main
jobs:
    deploy:
        runs-on: ubuntu-latest
        steps:
            - name: checkout
              uses: actions/checkout@v2
            - name: prepare
              run: |
                mkdir -p build
                touch build/.nojekyll
            - name: pandoc
              uses: docker://pandoc/core:2.12
              with:
                args: >-
                  --standalone
                  --output=build/index.html
                  --metadata title="Hello, Pandoc"
                  README.md
            - name: deploy
              uses: JamesIves/github-pages-deploy-action@4.1.0
              with:
                branch: gh-pages
                folder: build
```

On GitHub settings, go to `GitHub Pages`, and select the `gh-pages` branch.

Johan's example github https://github.com/jhidding/githubpages-docker-demo

You can see the final result: https://jhidding.github.io/githubpages-docker-demo/

if you update the `README.md` and push it to the repository, the "actions" will automatically run again and update the webpage with your new `README.md`.

### Containers in Research: Reproducibility

### Exercise (12 min) breakout (4 p/r) 

**Part 1 (5 min) Reproducibility with Containers: Good Practices**

Think of good practices for using containers for making research more reproducible. 

Write down. 12

Group 1: 
 * keep images/containers small,
 * use open source software as much as possible.
 * Only put stuff in image that are really required.
 * Keep small and modular, one docker image should focus on a single task if possible, containers can be stacked to create combined functionality
 * Specify correct version
 * Integrate with continuous testing/documentation

Group 2:
* specify the version number when building images
* use existing images when possible
* keep images as simple as possible

Group 3: 
* specify versioning of depencencies and not just the programs itself (running a year later will result in different container)
* make sure the documentation is more than just the Dockerfile (README or github pages)
* do not create multiple containers for just one task.
* Only include dependencies that are actually needed

Group 4:
* Still comment your code
* Tagging your images
* README file for your docker setup
* 

Group 5: 
* Don't install things you don't need
* Build on existing images
* Specify the version
* Document 
* Write comments in the dockerfile
* You could use a github page to document what the code does, etc
* Question: Difference between Dockerfile and a bash script downloading the docker image and running some commands?
* Question: How to add our data/code to the file???
    * You may be interested in using the COPY command in the Dockerfile
    * Can we go over this? This seems super useful!

**Part 2 (5 min) Container Granularity: Good and Bad**

What are the advantages and disadvantages of the two approaches to container granularity for research workflows described above? Think about this, discuss and write a few bullet points for advantages and disadvantages for each approach in the collaborative document. 

Group 1: 
 * Advantage of modular approach: container can be reused in multiple projects
 * Advantage modular container is easier tested and debugged
 * Disadvantage of small containers: it becomes more difficult to create a lot of fucntionalitry
 * Disadvantage might be dependencies between modules that are in separate containers

Group 2:
* with many smaller images, it is maybe easier to make each of them work properly, but then have to make sure they all work together in the end

Group 3: 
* where do you draw the line of multiple containers?
    * workflows, might work for data science, a criteria might be the need to scale up data processing tasks
    * software components, might work for developing tools
* if you have an output that is an input for the next part, you should different containers
    * for example mapping genes and annotation of genes. If you change your mapping program, you do not need to change the other container. you can just switch one piece of the puzzle. In biology the sequencing (for example) changes rapidly, and then you only change the first puzzlepiece and keep the rest intact.
    * summary: one task - one container 

Group 4: 
* it depends - we didnt reach a conclusion

Group 5: 
* what is Container Granularity???!!!

### Reproducible containers tips
 - Use the smallest possible container
   - Only include dependencies that you need
 - Use Open Source software as much as possible
 - Make your containers modular
 - Make sure you have enough documentation!
 - 
    
### Orchestration
Using more than one container:
 - [Docker compose](https://docs.docker.com/compose/) -- compose a workflow from different containers which run next to each other
 - [Kubernetes](https://kubernetes.io/) -- alternative solution to docker compose, developed by Google. Supported by many cloud platforms
 - [Docker swarm](https://docs.docker.com/engine/swarm/) -- Solution to scale out containers, multiple copies of the same container.
    
## 📚 Resources 

- [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
- [Docker Hub](https://hub.docker.com)
- [Uploading to Docker Hub](https://docs.docker.com/docker-hub/repos/)
- [Unix shell Software Carpentry Lesson](http://swcarpentry.github.io/shell-novice/)
- [Singularity lesson](https://carpentries-incubator.github.io/singularity-introduction/)
- [Pandoc the universal document converter](https://pandoc.org)
- [Documentation on GitHub Actions](https://docs.github.com/en/actions)
- [GitHub Pages deploy action](https://github.com/marketplace/actions/deploy-to-github-pages)
- [Pandoc action example](https://github.com/pandoc/pandoc-action-example)
- [Ten Simple Rules for Reproducible Research in Jupyter Notebook](https://arxiv.org/pdf/1810.08055.pdf)
- [Connecting your GitHub Repository to Zenodo and getting a DOI](https://guides.github.com/activities/citable-code/)

### Questions

- I have also used vagrant, do you know this tool, if yes, what would be the main difference between docker and vagrant?
    - Where Docker relies on the host operating system, Vagrant includes the operating system within itself as part of the package. One big difference between Docker and Vagrant is that Docker containers run on Linux, but Vagrant files can contain any operating system.
    - I used vagrant a very long time ago... They are similar, but Docker is a bit more light weight.
- I missed this a little bit: you can make multiple containers from one image, or multiple images from one container? (to have different containers for each task)
    - you can make multiple containers from one image.


- For the github pages task, when I do it, I need to go to "...github.io/docker/index.html" while the example doesn't need that "index.html". If I omit the "index.html", I get an error. Why do I need to have a web address to a file while the example doesn't need this?
    -  in your own repo you can go to the settings page and look where the github-pages site. There you will find the link to your webpage, which under the hood calls "index.html"


- Aside from running docker on caresius we were asked to run docker on our local gpu cluster. There are some security concerns with this since everything is basically run with root acces (that is what people told me). What are the solutions for this? Do you have some resources on how to safely excecute docker files on a cluster
- 
## Feedback
### Tip

* It can be nice to ask participants' experience with Linux distros and choose the example base image accordingly, e.g. instead of Alpine it can be Ubuntu, so that commands can be more easily found.
* The github pages part was awesome, it was a bit quick though and I would have liked to spend some more time on this.
* my github pages wasn't setup, I tried to follow along but my outcome didn't work because of this. Maybe either say don't follow along or have an optional preparation step prior to the workshop
* maybe have different workshops, based on subject? like biology (using fastq data) and other field that have a different datatype? so you have like a real life example?
* I rather have 3 "bigger" breaks compared to those 10 minute breaks (and have the reclaim focus)
* I would have liked more real examples and a bit less discussions (+1)
* I would suggest using one example of a research software (with different part like DB, code, data) and containerize it. I am still fuzzy about how to do it! +4
* Use a poll system (like strawpoll.com) to check for understanding. Just have one or two multiple choice questions to check for understanding. If everyone gets the questions wrong, then you know when you need to explain something in another way. I think this would be more effective than asking "did everyone understand?".
* Maybe a cheat sheet would have been nice. 
* Having a comprehensive overview over the code and solutions beforehand would have helped (although the shared doc also worked)
* Live coding started at 10.30. I would have liked to get started with coding quicker +1:+1:
* GitHub on MacOS only works when the xcode software is installed. However, the gitlab commands work without xCode. Can you please add that to your preparations?
* I would have liked to learn more about some of the topics covered only at the end, e.g. the docker compose. The github actions part was less relevant in my view. The github actions part was less relevant in my view. The github actions part was less relevant in my view. The github actions part was less relevant in my view.topics covered only at the end, e.g. the docker compose.topics covered only at the end, e.g. the docker compose.topics covered only at the end, e.g. the docker compose.topics covered only at the end, e.g. the docker compose. +1
* More discussion

### Top
* This interactive document worked nicely and keeps you engaged (+1)
* It was great to see how docker and github actions can work in practise. Thanks!
* breakout rooms were interesting to discuss things, but maybe implement them differently (only one question?)
* great start to get to know containers and use that knowledge to find more information
* Really practial guide for using docker. 
* pace was good for following along
* i liked the variation brought by breakoutrooms
* Great practical intro that was easy to follow  
* good pacegood pacegood pacegood pace
* Clear instructions
* The github pages example was great! I immediately saw a potential usecase for docker in git.
*  were 

## Post-workshop survey
https://www.surveymonkey.com/r/MGPBR6B