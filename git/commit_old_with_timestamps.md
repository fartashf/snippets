Git commit old files with their timestamp
=========================================
I had a set of files that unfortunately, I was not keeping track of their
changes with git. Actually, the only thing that mattered to me was their last
modification date because I usually would write them once and never change them
afterwards. Anyway, I wanted to put them in a git repo and preserve their
timestamp as well. So I wrote this one line of bash to do it:

```bash
find -name '*.prototxt' -exec stat --printf "%Y %n\n" '{}' \; | sort |\
awk '{print "git commit --date=\"`date -Ins --date=@"$1"`\" "$2" -m\""$2"\""}'
|\
while read line; do eval $line; done
```

A couple of things that made it difficult to write this:
- I could do this in a matter of seconds if I wanted to use VIM!
- git accepts a limited set of formats for --date.
- eval was needed to handle the evaluation of `` and other stuff.
- Some considerations are made to keep the order of commits
chronologically correct.
- I was used to enclosing the argument to -exec by single quotes but
maybe the style has changed or it's been a long time I haven't used
it!
- I had to git add all the files prior to doing this
