# code50

## Explanation

"code50" refers to the browser-based IDE of Visual Studio Code (aka "VS Code") built by the CS50 team at Harvard, utilizing Github Codespaces. Full documentation [here](https://cs50.readthedocs.io/code/).

## FOR EACH SECTION, READ EVERYTHING BEFORE YOU DO ANYTHING

Leave this window on the left half of your screen so that you can READ the directions.

Open a new window on the right half of your screen so that you can FOLLOW the directions.

Go to [code.cs50.io](https://code.cs50.io/) and login with your Github account

## Setting up an SSH key between code50 and Github

#### Configuring your user info

* In your command line, type the following: `git config --global user.email "you@example.com"`
  * Don't copy/paste.
  * Remember to use YOUR email address.
  * YES, you need the quotes.
  * Example: `git config --global user.email "johnd1234@hstat.org"`
* Then type `git config --global user.name "Your Name"`
  * Example: `git config --global user.name "John Doe"`

#### Generating and connecting an SSH key
* Copy/paste the following:
* `echo -e "\n" | ssh-keygen -t rsa -N ""`
* `cat ~/.ssh/id_rsa.pub`
  * Copy _all_ of the result to your clipboard (it should start with `ssh-rsa`)
* Go to https://github.com/settings/ssh/new
  * Title: ide50
  * Key: paste your ssh key
  * Press the green **Add SSH key** button
* Back in your cs50 IDE, copy/paste the following
```
echo 'Host github.com' >> ~/.ssh/config
echo ' Hostname ssh.github.com' >> ~/.ssh/config
echo ' Port 443' >> ~/.ssh/config
echo ' StrictHostKeyChecking no' >> ~/.ssh/config
ssh -T git@github.com
echo

```
* If you still see the last command in your terminal, press <kbd>ENTER</kbd>
You should see
> Hi "username"! You've successfully authenticated, but GitHub does not provide shell access.

**You're done setting up SSH keys! Now you can easily push to Github.**
<br>
<br>

_WARNING: ONLY if you made a mistake, type this command to DELETE your SSH keys and start over:_

`rm -rf ~/.ssh`

