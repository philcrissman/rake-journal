# Writing

Just done up in folders:

```
2016 -|
      |- feb -|
      |       |- 29/notes.markdown
      |- mar -|
      |       |- 01/notes.markdown
      |       |- 02/notes.markdown
```
  
... etc.

Each "day" folder will (probably) have at least a `notes.markdown` file. Maybe other files. Could be writing drafts. Maybe scripts?

That's about it.

--- 

## Rake tasks

### stats

The default rake task is called `stats`. If you just run `rake`, `rake stats` will run, and will calculate the word count for each day's folder in the writing directory, and return an average words/day.

```
> rake
Words for writing/2016/feb/29: 293
Words for writing/2016/mar/01: 301
Words for writing/2016/mar/02: 515
Words for writing/2016/mar/03: 610

Average words/day: 429
```

### today

If you run `rake today` it will create (if needed) the directories for `./YYYY/mon/DD/` and touch an empty file named `notes.markdown` in that directory.

```
> rake today
* Ensure directory writing/2016/mar/03 exists
* Created writing/2016/mar/03/notes.markdown
```

### newfile

If you run `rake newfile somefile`, it will create `./YYYY/mon/DD/somefile.markdown`.

```
rake newfile algorithms
* Ensure directory writing/2016/mar/03 exists
* Created writing/2016/mar/03/algorithms.markdown
```
