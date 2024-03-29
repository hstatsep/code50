# code50

#### [Video](https://www.youtube.com/watch?v=Y9IyXRUw6Yk) going through these directions

## Explanation

"code50" refers to the browser-based IDE implementation of Visual Studio Code (aka "VS Code") built by the CS50 team at Harvard, utilizing Github Codespaces. Full documentation [here](https://cs50.readthedocs.io/code/).

Go to [code.cs50.io](https://code.cs50.io/) and login with your Github account.

## Working in the correct directory

By default, **code.cs50.io** will load a codespace at a directory that does _NOT_ support `git` command. This is the 10-digit unique ID associated with your account, and we need to work in the parent directory. Though you could `cd ..` from the terminal, nothing in the file explorer on the left changes.

```bash
/workspaces/2F1224918 # the directory that loads by default (different ID)
/workspaces/ # the directory we need to work in
```

### Option 1
Simply entering `code /workspaces` into the terminal will launch a new codespace (make sure you close your old one!).
NOTE: It will ask you to confirm. Type `y` then press <kbd>ENTER</kbd>.

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
* If you are working on a shared computer, you can put the URL into a permanent URL shortener such as tinyurl.com (NOT yellkey). You will still be prompted to login with your Github account.

## Setting up an SSH key between code50 and Github

It is recommended that you leave this window on the left half of your screen so that you can READ the directions. Open a new window on the right half of your screen so that you can FOLLOW the directions.

### Configuring your user info
* In your command line, type the following: `git config --global user.email "you@example.com"`
  * Don't copy/paste.
  * Remember to use YOUR email address.
  * YES, you need the quotes.
  * Example: `git config --global user.email "johnd1234@hstat.org"`
* Then type `git config --global user.name "Your Name"`
  * Example: `git config --global user.name "John Doe"`
* Finally, copy/paste this: `git config --global pull.rebase false`

### Generating and connecting an SSH key
* Copy/paste the following:
* `echo -e "\n" | ssh-keygen -t rsa -N ""`
* `cat ~/.ssh/id_rsa.pub`
  * Copy _all_ of the result to your clipboard (it should start with `ssh-rsa`)
* Go to https://github.com/settings/ssh/new
  * Title: code50
  * Key: paste your ssh key
  * Press the green **Add SSH key** button
* Back in your IDE, copy/paste the following
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

_WARNING: **ONLY** if you made a mistake, type this command to DELETE your SSH keys and start over:_

`rm -rf ~/.ssh`


### Preventing auto-pushing

There is an extension installed that we need to disable (otherwise work will be auto-pushed to Github, and we don't want that).

* Left sidebar: **Extensions** (looks like a 4-piece block with one piece broken off)
* Type in: `gitdoc`
* Click on the **gitdoc** that appears
* Click **Uninstall** (not _disable_)
* You should now refresh your browser

### !!!!! IMPORTANT !!!!!
```diff
- This is a FREE codespace. 
- One limitation is that if you go several weeks without using it, 
- you will get an email warning you that your codespace will be deleted (reset) if you don't login. 
- So just make sure you login occasionally (i.e. over the summer if you're not actively using it), 
- and make sure you are checking your email so that you get the warning before it's too late!
```

**You're all done!** Your IDE is set up and ready to use. Everything below contains helpful hints on how to use your IDE.

---

## Previewing

### Markdown

Simply click the preview icon in the top-right corner of your open markdown file to preview side-by-side.

![](open-preview.png)

### HTML

In your terminal, run `http-server` at the parent directory of the HTML file you would like to preview (this will run a **temporary** preview of the HTML files you are serving, and isn't meant for long-term sharing/hosting). 

You will see something like:
```
Available on:
  https://username-code50-12345678-7w9q5j9thxgr4-8080.githubpreview.dev
Hit CTRL-C to stop the server
```
Command+click (Windows: control+click) on the URL that appears. Click the HTML file you wish to preview.

You can edit your code (it autosaves), then just reload the preview.

When you are done, press `CTRL+C` in your terminal to stop the temporary server.

## Other

### Opening files from the terminal

Simply use `code <file>` (without `<>`) to open a file, i.e. `code index.html` to open the file in the text editor.

### New Terminal

Did you lose your terminal? Launch a new one by pressing the menu icon in the top-left corner > `Terminal` > `New Terminal`.
