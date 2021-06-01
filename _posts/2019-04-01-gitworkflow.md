---
layout: post
title: My blogging workflow with Git
published: true
tag: Git
---



Just my blogging workflow.




1. Configure `git`
```bash
git config --global user.name "Murpholinox Peligro"
git config --global user.email "murpholinox@gmail.com"
git config --global core.editor vim
```
2. Clone blog repository
```bash
cd
mkdir Repos
# Old way to clone a repo
git clone https://github.com/murpholinox/murpholinox.github.io.git blog
# New way to clone a repo, with SSH
git clone git@github.com:murpholinox/murpholinox.github.io.git blog
```

> Update: new way is more secure, but you have to generate your SSH keys and add them to GitHub. You can find the instructions  [here]({% post_url 2020-05-01-addsshkeytogit %}).

3. Write post in `md` format
```bash
cd blog/
vim _posts/YYYY-MM-DD-title.md
```


4. Exit `vim`, then 
```bash
git add .
git commit -m 'Usefulcomment'
git push
```
Will ask for user id and password if cloning with the old way or passphrase if cloning with the new way.

If we edit something within GitHub then at our local repository we need to do `git pull`.
