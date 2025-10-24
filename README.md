# start repository

Type this into your directory to start your repo.

1. git init

# local configuration

Sometimes configuring git can be a challenge 
but it is only matter of time until it gets easier

-- reading out global config (with this one we can manage
lots of stuff like our user , credentials , init branch name , aliases , etc... ) --

1. **check your credentials**
1. nano ~/.git-credentials
2. git config --global -e

# Alias !

When we type commands in git it can get really depressing
as the command gets longer and longer so we can use something
called alias

-- setting aliases --

1. git config --global alias.**name** **"alias-function"**

example : 

git config --global alias.s "status --short"

(In this line we are replacing git status --short for git s)


# add files to the stage

To add files we have some options that we can use.

-- option A --

1. git add **file**

-- option B --

1. git add **directory**

-- option C --

1. git add . 

(this one adds all files from the current directory)


-- option D --

1. git add . -u

(this one adds all files , tracked and untracked)


-- option E --

1. git add *.* **file extension**

(this one is to add files with certain extensions)


# logs !

There are multiple ways to see logs , but we will see this
briefly due lack of my precious time

-- option A (the easiest one)

1. git log 

-- option B (crafting aliases)


1. git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
2. git lg


# how to revert my files in case i fucked up everything ?

Reverting is not the same as Reseting , when you revert
using checkout you keep the head attached to the last commit.

so if you checkout some hash , you are not actually taking your
project there, you are just CHECKING the code in that specific time.

what??

yes , that means your project is still fucked up and the HEAD keeps pointing
towards your fucked up commit.

to fix this see the resets! part.

-- option A --

1. git checkout -- .
(this line reverts our files to the last commit)

-- option B --

1. git log 
2. spot the hash of your target commit
3. git checkout **hash**


# commit 

-- option A --

1. **Add the files using one of the add options i taught you**
2. git commit -m **"message"**

-- option B -- 

1. git commit -am **"message"**
(This one is like doing => git add . => git commit -m "example")

# ammend commits

-- option A -- 
1. **make some wrong commit messages XD**
2. git commit --amend
(This one lets you correct your last commit message)

-- option B --

1. git commit --amend -m **"message"**
(This one is the same as the previous one but shorter and without GUI) 


# resets !

In this part we can actually move our whole project to another
instance of time and not just see the code but actually materializing
it into something.

-- option A --

1. git reset --soft HEAD^
(This makes the HEAD points towards the previous commit)

-- option B -- 

ranges : 

"soft => resets but keeps the file on stage"
"mixed => resets , doesn't keep the file on stage"
"hard => resets, destroys everything , rebuilds from zero"

1. **get the hash of your fucked up commit**
2. git reset **--range** **hash**
(This makes the HEAD points towards the hash)
