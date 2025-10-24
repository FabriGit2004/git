
This is a brief git cheatsheet made by me to help you guys understand some concepts. :)

# start repository

"""

Type this into your directory to start your repo.

"""


1. git init

# local configuration

"""
Sometimes configuring git can be a challenge 
but it is only matter of time until it gets easier

"""

-- reading out global config (with this one we can manage
lots of stuff like our user , credentials , init branch name , aliases , etc... ) --

1. $ check your credentials
1. nano ~/.git-credentials
2. git config --global -e





# Alias !

"""

When we type commands in git it can get really depressing
as the command gets longer and longer so we can use something
called alias

"""

-- setting aliases --

1. git config --global alias.$name $"alias-function"



example : 

git config --global alias.s "status --short"

(In this line we are replacing git status --short for git s)


# add files to the stage

""" 

To add files we have some options that we can use.

"""

-- option A --

1. git add $file


-- option B --

1. git add $directory


-- option C --

1. git add . 

(this one adds all files from the current directory)


-- option D --

1. git add . -u

(this one adds all files , tracked and untracked)


-- option E --

1. git add *.$file extension

(this one is to add files with certain extensions)


# logs !

"""

There are multiple ways to see logs , but we will see this
briefly due lack of my precious time

"""

-- option A (the easiest one)

1. git log 

-- option B (crafting aliases)


1. git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
2. git lg


# how to revert my files in case i fucked up everything ?

"""
Reverting is not the same as Reseting , when you revert
using checkout you keep the head attached to the last commit.

so if you checkout some hash , you are not actually taking your
project there, you are just CHECKING the code in that specific time.

what??

yes , that means your project is still fucked up and the HEAD keeps pointing
towards your fucked up commit.

to fix this see the resets! part.

"""


-- option A --

1. git checkout -- .
(this line reverts our files to the last commit)

-- option B --

1. git log 
2. spot the hash of your target commit
3. git checkout $hash


# commit 

-- option A --

1. $Add the files using one of the add options i taught you
2. git commit -m $"message"

-- option B -- 

1. git commit -am $"message"
(This one is like doing => git add . => git commit -m "example")

# ammend commits

-- option A -- 
1. $make some wrong commit messages XD
2. git commit --amend
(This one lets you correct your last commit message)

-- option B --

1. git commit --amend -m $"message"
(This one is the same as the previous one but shorter and without GUI) 


# resets !

"""

In this part we can actually move our whole project to another
instance of time and not just see the code but actually materializing
it into something.

"""

-- option A --

1. git reset --soft HEAD^
(This makes the HEAD points towards the previous commit)

-- option B -- 

ranges : 

"soft => resets but keeps the file on stage"
"mixed => resets , doesn't keep the file on stage"
"hard => resets, destroys everything , rebuilds from zero"

1. $get the hash of your fucked up commit
2. git reset $--range $hash
(This makes the HEAD points towards the hash)

!! IMPORTANT !!

After doing this your HEAD moves , this means all commits after
the commit hash you will be pointing to are going to get OBLITERATED.
be cautious before doing this or you will have to reflog.

(check reflogs!)


# reflogs !

"""
Sometimes everything gets fucked , but git knows this
so it keeps the whole registry of changes even if destroyed
you can access this like the commit log.

"""

1. git reflog
2. git reset --hard $hash

We use this to move our whole project to a certain time reference.



# Rename !

"""

When we want to rename a file we should do it in the stage.

"""


1. git mv $old file OR  old directory $new file OR new directory

(we do this to keep git informed about our changes)

Important!!

If we use 'mv' instead of 'git mv' there is trazability.


# Delete !

"""

This is the same as renaming , always keep git informed
and don't use local linux commands when deleting because
git can lose track of the whole history of your file.

"""


1. git rm $-param $file or directory




# Branches !

"""

We should always create a new branch for each new functionality
we add to our system so if it breaks it will just break in our localhost.


depending in how screwed our branch is , when we merge we can get
these three outputs:

1- fast forward :
        the master branch doesn't have modified files that our external branch
        doesn't know and depends of.

2- Union merge :
        in this case we have modified files in our master branch that affect
        our external branch but git is capable of solving because the mods
        don't interfere with the incoming branch.

3- Conflict (worse case scenario) :
        when git gets into conflict state the whole merge will depend on us
        for this cases is good to have a good scope of the whole logic before
        doing something , because when there is conflict it means that some guy A
        has modified a file that has already been modified by some guy B and you
        must decide which code remains.




"""


1. git branch $name of the branch
2. git checkout $name of the branch
3. $do changes
4. $go back to master or main once you have finished
5. once in main or master => git merge $name of the branch

(our outcome will depend on how fucked up everything is.)

best case scenario you get a fast-forward.



# tags !

"""

Tags are really important when we want to display our LTS
or whatever code we consider stable, we add tags to commits
so our github can display them like important commits of
east access.

"""

1. git tag -a $tag name $hash -m $tag message



# stash !

"""

Stashes are little vaults where we keep our current changes in case of emergencies
for example:

Lets say you are making a new functionality for your project but your PM wants you to deploy 
some image right now , in that special case you could use stash to keep your changes stored
and post the cat image.

From my perspective i don't recommend using too many vaults simultaneously.
Also use branches to ensure a good flow.

"""


1. git stash

(saves current commit as a WIP)

2. git stash list

(shows all of your stash vaults)

3. git stash popim not a bitch

(recovers the first stash in your stash list)


!! important !!

you can get a stash conflict if : 
        - you stashed file changes.
        - make new changes again and commit.
        - stash pop

this will 100% generate conflict so be carfeul while managing 
your stashes.
