# Version control with Mercurial

Resources
---------

* [Mercurial:`The`Definitive`
`Guide](http://hgbook.red-bean.com/read/)- an online copy of Sullivan book published by O'Reilly.
* [Mercurial`
`wiki](http://mercurial.selenic.com/wiki/)\
* [HgInit`tutorial](http://hginit.com/index.html)

Installing and configuring
--------------------------

- Install in debian with `*`apt-get`install`mercurial`*\
- Create ~/.hgrc and add the following lines:`

[ui]
username = Firstname Lastname `<username@somewhere.com>\
verbose = True`

## Creating a repository

First enter the directory that needs version control and initialize the
repository

cd ~/projectdirectory
hg init`

This will create the .hg directory containing the repository in
\~/projectdirectory

Next, add the files in the \~/projectdirectory to the repository
~~~

hg add  #schedule all files in ~/projectdirectory to be added to the repository
hg add file1, file2  #or add files to the repository individually`

~~~

The queue of files added to the repository can be viewed with *hg
status*.

Then, commit the initial version of these files ~~~

hg commit  #this will pop up an editor for you to add a commit description
hg commit -m "This is the initial commit of these files"  #or add the message directly from the commandline`

~~~

Use *hg log* to view a history of commits to the repository (most recent
commits are at the top).

## Make and commit changes

 **Commits should occur whenever substantial changes are made to a
        file.** This would include new features, creation of new
        scripts or functions, changes in data sources, or other
        substantial changes in the function or output of data
        analysis code.

Once changes are made to a file in the directory, *hg status* will show
which files are modified
`greg@gm-thinkpad:~/data/data_analysis/project1$`vim`m/file1.m`
`greg@gm-thinkpad:~/data/data_analysis/project1$`hg`status`M`
`m/file1.mThe M at the left indicates that the file has been modified.
Other possible markers here are "!", meaning the file is missing, or
"?", meaning the file is unknown (is newly created or not added).

When these files are commited, *hg log* will display the changes
~~~ greg@gm-thinkpad:\~/data/data\_analysis/project1\$ hg commit
-m 'Added some new stuff to file1.m' m/file1.m committed changeset
1:0048e1a6cd8b greg@gm-thinkpad:\~/data/data\_analysis/project1\$ hg log
changeset: 1:0048e1a6cd8b tag: tip user: Firstname Lastname
<username@somewhere.com> date: Thu Dec 29 14:35:06 2011 -0700 files:
m/file1.m description: Added some new stuff to file1.m

changeset: 0:d0eea9c4d2d5 user: Firstname Lastname
<username@somewhere.com> date: Wed Dec 28 14:10:55 2011 -0700 files:
m/file1.m m/file2.m otherdatadir description: Initial commit of files

~~~

## Tracking, removing, renaming, or ignoring files

 **hg add //file1//**

* Adds a new file to the repository On the next commit this file will be added to the repository and tracked from then on. `

 **hg remove //file1//**

* Will delete the file and cause it to stop being tracked by mercurial. If a file has been deleted without using `*`hg`
`remove`*the file will be considered missing (has a ! under `*`hg`
`status`*`) by mercurial. Removing files does not remove their history, so they will reappear if you return to a changeset where they were still tracked. If you remove a file without `*`hg`
`remove`*and `*`hg`
`status`*reports it as missing, you can run `*`hg`remove`
`--after`*to tell Mercurial about it after the fact.`

 **hg addremove**

* This is a combination command that adds untracked files and marks missing files as removed.`

 **hg copy //file1 new\_file1//**

* Makes a new copy of a file. When you copy a file using this command, Mercurial makes a record of the fact that the new file is a copy of the original file. It treats these copied files specially when you merge your work with someone else’s.`

 **hg rename //file1 file2//**

* Mercurial makes a copy of each source file, then deletes the original and and marks it as removed. Using `*`hg`
`status`
`-C`*will show the origin of the renamed file (since deleted). You can also tell Mercurial about a rename after the fact with `*`hg`
`rename`--after`*`.`

### The .hgignore file

The working directory of a Mercurial repository will often contain files
that shouldn't be tracked (backup copies, binary files, etc). These
files can be listed in a plain textfile within that directory called
***.hgignore***, and mercurial will ignore these files.

An example .hgignore file: <code>

1.  use glob syntax (Shell style).

syntax: glob

-   .elc
-   .pyc
-   \~

1.  switch to regexp syntax (Regular expression as in Perl/Python).

syntax: regexp \^\\.pc/ ~~~

## Viewing or changing between previous revisions

#### Revert

The command ***hg revert*** will revert the directory back to
**the version at the last commit.** This will restore any files that
were deleted, and will restore changed files to their state at the last
commit. When files are reverted, the current working version will be
resaved with a *.orig* extension.
`greg@gm-thinkpad:~/data/data_analysis/project1$`vim`m/file1.m`#`
`edit`the`file`greg@gm-thinkpad:~/data/data_analysis/project1$`
`hg`revert`--all`saving`current`version`of`m/file1.m`as`
`m/file1.m.orig`#`edits`since`the`last`commit`will`be`
`saved`in`the`.orig`version`reverting`m/file1.m`#`
`file1.m`goes`back`to`its`previous`stateNote that it is
also possible to revert individual files (change --all to desired
filename).

#### Update

The ***hg update*** command allows movement between the various
revisions of the directory. Revisions are easily viewed in the log as
the first number of the changeset. ~~~
greg@gm-thinkpad:\~/data/data\_analysis/project1\$ hg update -r 0
resolving manifests getting m/file1.m 1 files updated, 0 files merged, 0
files removed, 0 files unresolved

1.  this command will update the directory to its state at the
    original commit. Only m/file1.m will change
2.  

hg update -r 1 # takes us back to the current commit version (see log)
- hg update without arguments will also do this ~~~

#### Rollback

The **hg rollback** command has the capability to undo one commit,
as long as that commit hasn't been pushed to anyone else.

#### Examine changes

Specific changes between revisions can be viewed with the diff command,
or by serving up the repository's history on mercurial's built in
webserver.

### Using diff

~~~ greg@gm-thinkpad:\~/data/data\_analysis/project1\$ hg diff
-r 0 m/file1.m # -r 0 means compare current version to original commit
version diff -r d0eea9c4d2d5 m/file1.m --- a/m/file1.m Wed Dec 28
14:10:55 2011 -0700 +++ b/m/file1.m Thu Dec 29 16:14:30 2011 -0700 @@
-4,6 +4,9 @@

`%`

-% data is from CNisotopedata files in rawdata folder. # this line
removed -% # and this one + # this and the next 2 lines added +I added
this line +

`clear;          % clear memory
`close all;      % clear any figures
`fignum=0;       % used to increment figure number for plots`

~~~

### Use an external diff program

Make sure *extdiff* extension is enabled in *\~/.hgrc*, then:

hg extdiff -p vimdiff -r 63 processed_data/wyear_climatesummary.txt`

### The webserver

~~~ greg@gm-thinkpad:\~/data/data\_analysis/project1\$ hg serve
listening at <http://gm-thinkpad.pronghorns.net:8000/> (bound to
\*:8000)

1.  directing a webserver to this
    address (http://gm-thinkpad.pronghorns.net:8000/) will show a web
    interface where all revisions
2.  visible in different formats (diff, changeset, etc)

~~~

## Working with multiple repositories

There are several use-cases in which the following commands are useful:

- A team of developers working on the same project must share changes between their local repositories and a central repository.
- In solo development it may be useful to make an experimental clone of the repository for testing changes. If successful, these changes can be pushed back to the main.`

### Commands

* **hg clone** makes a copy of an entire repository (including all files and directory structures).
  * Results in a testing branch for solo development, or local working copies of a team project.
* **hg outgoing** lists changes in current repository waiting to be pushed
* **hg incoming** lists changes in remote repository waiting to be pulled (new changesets in central repo since clone, or last pull)
* **hg paths** shows a list of all known remote repositories, including a default for pushing changesets.
* **hg push** will push new changes from one repository to another.
  * This could be a central or local repository used to clone the current working repository
* **hg pull** pulls in changesets from a central or local repository (the parent of the current one)
* **hg parent** shows which changeset(s) you are working off of in your current repository.
* **hg merge** merges the changes in two heads (ie. when there are two competing changesets added to the repository)`

### Example 1

In this example, a solo developer makes a clone of a project repository
to test changes. Some changes are then pushed back to the original
repository, while some remain in the testing branch, which will have
some kind of different functionality.

`greg@gm-thinkpad:~/data/data_analysis/project1$`hg`clone`.`
`../project1_testing`#`clone`the`current`repository`into`
`a`testing`repository`updating`to`branch`default`
`resolving`manifests`getting`datadir`getting`m/file1.m`
`getting`m/file2.m`getting`otherdatadir`4`files`updated,`
`0`files`merged,`0`files`removed,`0`files`unresolved`
`greg@gm-thinkpad:~/data/data_analysis/project1$`ls`../`
`hiddencanyon`SNOTELdata`project1`project1_testing`#`there`
`is`now`another`repository`(project1_testing)`alongside`the`
`original`greg@gm-thinkpad:~/data/data_analysis$`cd`
`../project1_testing/`
`greg@gm-thinkpad:~/data/data_analysis/project1_testing$`ls`#`it`
`is`identical`to`the`original`m`datadir`otherdatadirNow,
changes can be freely made in the testing branch, and those that work
can be pushed back to the original. ~~~
greg@gm-thinkpad:\~/data/data\_analysis/project1\_testing\$ vim
m/file1.m greg@gm-thinkpad:\~/data/data\_analysis/project1\_testing\$ hg
st M m/file1.m
greg@gm-thinkpad:\~/data/data\_analysis/project1\_testing\$ hg diff diff
-r ed43a5a8e664 m/file1.m --- a/m/plot\_SNOTELsurvey\_CN.m Fri Dec 30
06:46:04 2011 -0700 +++ b/m/plot\_SNOTELsurvey\_CN.m Fri Dec 30 07:02:05
2011 -0700 @@ -3,6 +3,9 @@

`% Plots of C, N, and isotope data for SNOTEL survey sites
`%
`% Uses isotope data in soildata/CNisotopedata15sites.csv`

+ +This is my new testing code +it does cool stuff

`clear;          % clear memory
`close all;      % clear any figures`

greg@gm-thinkpad:\~/data/data\_analysis/project1\_testing\$ hg commit -m
"added a cool new feature" m/file1.m committed changeset 5:569e890e2f49
greg@gm-thinkpad:\~/data/data\_analysis/project1\_testing\$ hg outgoing
comparing with /home/greg/data/data\_analysis/project1 searching for
changes changeset: 5:569e890e2f49 tag: tip user: Greg Maurer
<greg@pronghorns.net> date: Fri Dec 30 07:02:25 2011 -0700 files:
m/file1.m description: added a cool new feature

greg@gm-thinkpad:\~/data/data\_analysis/project1\_testing\$ hg push
pushing to /home/greg/data/data\_analysis/project1 searching for changes
1 changesets found adding changesets adding manifests adding file
changes added 1 changesets with 1 changes to 1 files ~~~

If, in the meantime, commits have been made in the original repository,
this push will result in **two "heads"** to the repository. The
changesets in the original repo and the "testing" changeset that has
just been pushed will have to be **merged**.

### Example 2

In this example clones of a central repository are made by a team.
Mercurial helps to exchange and merge changes that are made between the
various local repos and the central repository.

[Covered here](http://hginit.com/02.html)

## Pushing to a Git repository (GitHub)

The [hg-git](http://hg-git.github.com) plugin is needed for
this.

$ easy_install hg-git   #first install hg-git
`

Create a repository on GitHub and save an SSH Key there using [these
instructions](http://help.github.com/linux-set-up-git/)

$ cd repositoryname # (a Mercurial repository)
$ hg bookmark -r default master # make a bookmark of master for default, so a ref gets created
$ hg push git+ssh://git@github.com/gremau/repositoryname.git
$ hg push`
