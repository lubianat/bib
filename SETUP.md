# Creating a new dashboard and workstation

These instructions detail how you can set up Wikidata Bib as your literature manager from the [`wikidatabib/rootstock`](https://github.com/wikidatabib/rootstock).
The process is largely manual, but you only have to perform it once for your dashboard. 

Currently, the repository has only been tested on Linux, and it might not work on other platforms. 

# Manual configuration

First, you must configure two environment variables (`OWNER` and `REPO`).
These variables specify the GitHub repository for the manuscript (i.e. `https://github.com/OWNER/REPO`).
Make sure that the case of `OWNER` matches how your username is displayed on GitHub.
In general, assume that all commands in this setup are case-sensitive.

```sh
# GitHub username or organization name (change from wikidatabib)
OWNER=wikidatabib
# Repository name (change from bib, if desired)
REPO=bib
```

## Create repository

**Execute the remaining commands verbatim.**
They do not need to be edited (if the setup works as intended).

Next you must clone `wikidatabib/rootstock` and reconfigure the remote repositories:

```sh
# Clone manubot/rootstock
git clone --single-branch https://github.com/wikidatabib/rootstock.git $REPO
cd $REPO

# Configure remotes
git remote add rootstock https://github.com/wikidatabib/rootstock.git

# Option A: Set origin URL using its web address via SSH
git remote set-url origin git@github.com:$OWNER/$REPO.git
```

Then create an empty repository on GitHub. 
You can do this at <https://github.com/new> or via the [GitHub command line interface](https://github.com/cli/cli) (if installed) with `gh repo create`.
Make sure to use the same "Owner" and "Repository name" specified above.
Do not initialize the repository, other than optionally adding a Description.
Next, push your cloned manuscript:

```sh
git push --set-upstream origin main
```

# Install requirements

Wikidata Bib depends on Python3 and some Python3 packages to work. 

```bash
pip3 install -r requirements.txt
```

It also uses Virtual Studio Code for note management, so make sure you have it installed too. 
See the instructions for that [here](https://code.visualstudio.com/docs/setup/linux).


# Read your first article

To trigger the dashboard, and get the magic started, read your first article with the system. 
For that, you have to set permissions for the scripts in the platform:

```bash
chmod +x wread
chmod +x pop
chmod +x wadd
chmod +x wlog
```

Now, run "wread" to get started:

```bash
./wread Q18507561
```

Don't worry about any errors that might pop up at this step. 

A vscode window for notes will appear on your screen.
It has some categories and links, but don't worry about that just now. 
You can check the [USAGE.md](./USAGE.md) file for instructions on that.


The file has been created under the `notes` folder. 
Save it, and come back to the terminal. 

On the terminal, you may now run "./wlog", which will commit your reading, and push it to GitHub.

 

# Credit

* This SETUP was adapted from Manubot's rootstock (<https://github.com/manubot/rootstock>), which you should definitely check out. 