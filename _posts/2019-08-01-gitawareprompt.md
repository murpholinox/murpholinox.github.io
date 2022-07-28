---
layout: post
title: How to have a Git-aware prompt?
published: true
tag: git
---

The next `bash` script provides command completion to `git` commands and a `git`-aware prompt.

```bash
# Usage:
# Copy into a file called `git.sh`
# From your terminal do `chmod u+x git.sh`
# and use as `bash git.sh`
cd $HOME
wget -O .git-completion.bash https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
wget -O .git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
echo '# Git completion' >> .bashrc
echo '. ~/.git-completion.bash' >> .bashrc
echo '# Git-aware prompt' >> .bashrc
echo '. ~/.git-prompt.sh' >> .bashrc
echo 'export GIT_PS1_SHOWDIRTYSTATE=1' >> .bashrc
printf '%b\n' "export PS1='\w\$(__git_ps1 \" (%s)\")\\$ '" >> .bashrc
printf  'done!\n'
exit
```

From [here](https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Git-in-Bash).
