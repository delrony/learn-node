# Save learn progress with docker and git

Imagine that we start reading a book in office and working along with the examples of the book. Just before leaving the office, we want to save our progress and want to continue from home. How can we do this? Here is a simple example.

I am reading a book about a Javascript library - React. To try the examples of the book, I first clone my `learn-node` repository from [Github](https://github.com/delrony/learn-node).

```bash
~$ git clone https://github.com/delrony/learn-node
~$ mv learn-node react
```
As I am going to learn react, I change the folder name to 'react'.

Now, I need to install Nodejs in my server. Instead of installing Nodejs in my server, I create a Docker image for Nodejs.
```bash
~/react$ cd docker
~/react/docker$ docker build -t ronyhuda/learn-react .
```
Change the name 'ronyhuda' to your docker hub's username.

My working directory is 'react/', where I create the files to follow the examples of the book.

Now I need to run a container for ronyhuda/learn-react image. First, I change the image name in docker-compose.yml file. Then I start the container.
```bash
~/react$ docker-compose up -d
```
I login to the container to prepare my react app:
```bash
~/react$ docker exec -it react_learn_1 bash
```
The first thing I want is to install react.
```bash
/var/learner$ yarn add react
```
This adds two files - package.json and yarn.lock. It also creates a directory, called node_modules. I don't want to add node_modules directory in repository. So, I create a .gitignore file and write the directory name to the file.
