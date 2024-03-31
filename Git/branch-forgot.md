# Branch pulling oblivion

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

```shell
git branch↵
* master
```

 Oops! I'm on master...

```shell
git status↵
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   xxxx
        deleted:    xxxx        
```

...and there are many changes

![pix](../pix/branch-forgot.png)

```shell
git switch -C feature2↵
Switched to a new branch 'feature2'
```

Ah. Relieved. I saved my change into a new branch.
