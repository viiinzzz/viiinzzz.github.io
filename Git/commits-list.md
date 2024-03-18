# List all commits

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

Do you need to provide a time-stamped list of all your commits in a project ?

![pix](../pix/report2boss.png)

Do it this way:

```bash
git log --pretty="format:%ad %s" --date="format:%Y-%m-%d %H:%M:%S" > commits-list.txt↵
```

> [!TODO]
>
> __Scenario__
> Imagine this is not a personal repo but a collaborative multiuser repo.
>
> __Question__
> How would I filter the logs for showing only my own commits ?
