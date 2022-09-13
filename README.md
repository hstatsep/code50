# code50

## Explanation

"code50" refers to the browser-based IDE implementation of Visual Studio Code (aka "VS Code") built by the CS50 team at Harvard, utilizing Github Codespaces. Full documentation [here](https://cs50.readthedocs.io/code/).

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
  * Title: code50
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

_WARNING: **ONLY** if you made a mistake, type this command to DELETE your SSH keys and start over:_

`rm -rf ~/.ssh`

## Working in the correct directory

By default, **code.cs50.io** will load a codespace at a directory that does _NOT_ support `git` command. This is the 10-digit unique ID associated with your account, and we need to work in the parent directory. Though you could `cd ..` from the terminal, nothing in the file explorer on the left changes.

```bash
/workspaces/2F1224918 # the directory that loads by default (different ID)
/workspaces/ # the directory we need to work in
```

### Option 1
Simply entering `code /workspaces` into the terminal will launch a new codespace (make sure you close your old one!).

### Option 2
Doing the command above essentially loads a new tab with a different URL. Here's the before/after:

Before:
<pre>
https://username-code50-12345678-7w9q5j9thxgr4.github.dev/?folder=%2Fworkspaces<b>%2F1224918</b>&vscodeChannel=stable
</pre>
After:
<pre>
https://username-code50-12345678-7w9q5j9thxgr4.github.dev/?folder=%2Fworkspaces&vscodeChannel=stable
</pre>

So the solution is to delete the **`%`** and your **10-digit ID** from the URL. The fastest way to do this is to double-click the 10-digit ID, then <kbd>DELETE</kbd> or <kbd>BACKSPACE</kbd> twice (to also delete the `%`).

#### Faster access in the future

* If you are working on your personal computer, you can bookmark this URL.
* If you are working on a shared computer, you can put the URL into a permanent URL shortener such as tiny.cc or bit.ly (NOT yellkey). You will still be prompted to login with your Github account.

## Previewing

### Markdown

Simply click the preview icon in the top-right corner of your open markdown file to preview side-by-side.

<svg>
	<path fill="currentColor" fill-rule="evenodd" d="M3 1h11l1 1v5.3a3.21 3.21 0 0 0-1-.3V2H9v10.88L7.88 14H3l-1-1V2l1-1zm0 12h5V2H3v11zm10.379-4.998a2.53 2.53 0 0 0-1.19.348h-.03a2.51 2.51 0 0 0-.799 3.53L9 14.23l.71.71l2.35-2.36c.325.22.7.358 1.09.4a2.47 2.47 0 0 0 1.14-.13a2.51 2.51 0 0 0 1-.63a2.46 2.46 0 0 0 .58-1a2.63 2.63 0 0 0 .07-1.15a2.53 2.53 0 0 0-1.35-1.81a2.53 2.53 0 0 0-1.211-.258zm.24 3.992a1.5 1.5 0 0 1-.979-.244a1.55 1.55 0 0 1-.56-.68a1.49 1.49 0 0 1-.08-.86a1.49 1.49 0 0 1 1.18-1.18a1.49 1.49 0 0 1 .86.08c.276.117.512.311.68.56a1.5 1.5 0 0 1-1.1 2.324z" clip-rule="evenodd"></path>
</svg>

### HTML

In your terminal, run `http-server` at the parent directory of the HTML file you would like to preview (this will run a **temporary** preview of the HTML files you are serving, and isn't meant for long-term sharing/hosting). 

You will see something like:
```
Available on:
  https://username-code50-12345678-7w9q5j9thxgr4-8080.githubpreview.dev
Hit CTRL-C to stop the server
```
Command+click on the URL that appears. Click the HTML file you wish to preview.

You can edit your code (it autosaves), then just reload the preview.

When you are done, press `CTRL+C` in your terminal to stop the temporary server.

## Other

### New Terminal

Did you lose your terminal? Launch a new one by pressing the menu icon in the top-left corner > `Terminal` > `New Terminal`.