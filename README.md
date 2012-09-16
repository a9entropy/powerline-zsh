Powerline style prompt for Zsh 
===============================

*This is a fork from https://github.com/milkbikis/powerline-bash*

A [Powerline](https://github.com/Lokaltog/vim-powerline) like prompt for Zsh:

![MacVim+Solarized+Powerline+CtrlP](https://raw.github.com/milkbikis/dotfiles-mac/master/bash-powerline-screenshot.png)

*  Shows some important details about the git branch:
    *  Displays the current git branch which changes background color when the branch is dirty
    *  A '+' appears when untracked files are present
    *  When the local branch differs from the remote, the difference in number of commits is shown along with '⇡' or '⇣' indicating whether a git push or pull is pending
*  Changes color if the last command exited with a failure code
*  If you're too deep into a directory tree, shortens the displayed path with an ellipsis
*  Shows the current Python [virtualenv](http://www.virtualenv.org/) environment
*  It's all done in a Python script, so you could go nuts with it

# Setup

* This script uses ANSI color codes to display colors in a terminal. These are notoriously non-portable, so may not work for you out of the box, but try setting your $TERM to xterm-256color, because that works for me.

* Patch the font you use for your terminal: see https://github.com/Lokaltog/vim-powerline/wiki/Patched-fonts

* Clone this repository somewhere:

        git clone https://github.com/carlcarl/powerline-zsh

* Create a symlink to the python script in your home:

        ln -s <path/to/powerline-bash.py> ~/powerline-zsh.py

  If you don't want the symlink, just modify the path in the .bashrc command below

* Now add the following to your .bashrc:
		
		function _update_ps1()
		{
			export PS1="$(~/powerline-zsh.py $?)"
		}

		precmd(){
			_update_ps1
		}