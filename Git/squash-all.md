# Squash it all

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

You reached the acme of coding and uzi-committed your repo all over ? Congratulations. Carry on the good job.

However all the damn intermediate steps are none-sense in the end.
Which writer keeps all the scrap papers balled up and thrown ?

> [!TIP]
> OK, OK, that's not the general mean of a git repo, history is useful. ...Sometimes it is not. Let's pretend.

Now you want to cleanup your branch history, I mean radically, do you ?

![pix](../pix/squash-all.png)

> [!WARNING]
This will **compact all** commits into a **single** one!
>
It is much more **radical** than the `squash` command because it goes beyond pull requests.

```bash
git switch main↵
#assuming we're on messy 'main'

# we'll do the following
# - ensure the 'backup' branch does not exist by deleting it
# - stage current changes and commit them
# - 'backup' branch with timestamp commit
# - reset 'main' onto that newly acquired 'backup' and push it

git branch -d backup; \
git add -A; \
git commit -m "last commit"; \
git checkout --orphan backup&& \
git commit -m "`date`"&& \
git switch main&& \
git reset --hard backup&& \
git push --force↵

#notice ; to continue whatever previously happened and && to stop in case of a prob
```

## Gentle squashing

Wanna be kind and squash only the current feature commits in a single before to send your PR ?

```bash
#let's say I add a new commit
git status↵
git add .↵
git commit -m "hello"↵
git push↵

#and I want to squash it with the previous
#ie to make 2-in-1
#without the commands `git rebase` nor `git merge --squash`
#HEAD~2 means last 2 commits, ie current and previous
git reset --soft HEAD~2 && \
git commit -m "hello" && \
git push -f↵
```

> [!WARNING]
> !!below does not working
> if anybody want to help me, I'd like to concatenate messages while squashing

```shell
git reset --soft HEAD~2↵
git commit --edit -m"$(git log --format=%B --reverse HEAD..HEAD@{1})"↵
git push -f↵

git rebase -i HEAD~2↵
```
