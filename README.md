# wrap

usage: wrap [width] [command]  
defaults:  
  width: 30  
  command: fmt  

Little app to wrap text and preserve lines breaks for
lines that are shorter that the specified width, which is
not done by `fmt`. This can be useful for piping into
other applications (such as `glow`) which don't fill.

For example, suppose you have a file `test2.md` like so:

```text
I was taught that the first three Presidents were

Washington
Adams
Jefferson
```

`fmt -w 30 <test2.md` generates

```text
I was taught that the first
three Presidents were

Washington Adams Jefferson
```

Whereas `wrap 30 <test2.md` generates

```text
I was taught that the first
three Presidents were

Washington
Adams
Jefferson
```

Finally, you can also specify the formatter. You might use
the `par` command to justify the text. So, for example,

```bash
wrap 40 "par -j" <<EOF
Four score and seven years ago our fathers brought forth
on this continent, a new nation, conceived in Liberty,
and dedicated to the proposition that all men are created
equal.

Now we are engaged in a great civil war, testing whether
that nation, or any nation so conceived and so dedicated,
can long endure.
EOF
```

generates:

```text
Four  score  and  seven  years  ago  our
fathers brought forth on this continent,
a new nation,  conceived in Liberty, and
dedicated  to the  proposition that  all
men are created equal.

Now we are engaged in a great civil war,
testing  whether  that  nation,  or  any
nation  so conceived  and so  dedicated,
can long endure.
```
