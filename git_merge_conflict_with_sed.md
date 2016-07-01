Git merge conflict
==================
There was this file with so many lines that git merge couldn't automatically 
resolve the problem and hence lots of blocks of conflict were written inside 
the file. The file was an ipython notebook with some useful results saved in 
it. Unfortunately, it was a couple of commits back and simply using checkout 
--ours or --theirs was not giving me the right output. However, I could see 
that the version I wanted to retain was the version referred to as HEAD inside 
the file. I tried correcting the file with VIM then but there were so many 
conflicts. So I used sed to simply get rid of the conflict messages. 

```bash
sed '/====/,/>>>>/d'
sed '/<<</d'
# Use -i to do this in place
```

This 
[link](https://nixtricks.wordpress.com/2013/01/09/sed-delete-the-lines-lying-in-between-two-patterns/) 
was helpful. 
