![logo](../pix/viiinzzz48.png){: style="float: left"}
[back to home](https://viiinzzz.github.io/HOME)

# List all commits

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
