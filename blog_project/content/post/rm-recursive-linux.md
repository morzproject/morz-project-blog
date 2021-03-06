+++
date = "2013-07-09T08:25:58+10:00"
draft = false
title = "Remove Files Recursively in Linux"

+++
Do you ever try `rm -r *.bak` and wonder why it is not working like it is supposed to? From the man page (man rm), the definition for `-r` is :
{{< highlight text >}}
r, -R, --recursive
              remove directories and their contents recursively
{{< /highlight >}}
<!--more-->
So basically `-r` is for directories and their contents recursively. In other words it only deletes recursively, not search recursively for things to be deleted.

A quick fix is simple :
{{< highlight shell >}}
find -type f -name '*.bak' -print0  | xargs -0 rm
{{< /highlight >}}