# aa_sqlite
## Whys and Wherefores

Lurking within the normal Python 2.x distribution is the sqlite3 import,
which is an amazingly powerful, no-server-required, mostly SQL
compatible database engine that can be used in any project without
restriction.

That's the up side. The down side is, as a fairly complete database,
there are many options and varied ways it can be used, and managing
actual database transactions isn't all that simple â to do it right,
even a single query takes about sixteen lines of code. And yes, if you
want maximum flexibility and the ability to use every feature in
sqlite3, that's how you should do it.

But. Most database operations are very straightforward. You want to
issue a single command to the database, or a query. Perhaps you want to
write a bunch of data and then commit it all at once so that the
database doesnât contain part of the data from a more complex
transaction. You need to know if something went wrong, and if it did,
what it was. Those are by far the most common use cases for me, and I
suspect thatâs true for others as well.

Frankly, it's difficult enough dealing with the SQL query language
itself. Why make actually using it harder than it has to be?

Another thing that can be inconvenient is the customary approach most
database engines, including sqlite, take towards retrieving query data.
It's done line by line, with the justification that this saves memory.
Ok, sure it does. But in these days of machines with gigabytes of RAM
available, does your database really need to be that conservative? The
answer is, not unless it is handling a very, very large amount of data.

There's a related issue as well. When a database fetches query results
one at a time, you can't check to see how many results you actually got,
because it actually doesn't know until it has fetched them all.

So aa_sqlite.py makes it easy to retrieve everything at once, complete
with an accurate count of row(s) retrieved. If you want to. It's just as
easy to use row by row, too.

Lastly, wouldn't it be nice if you had really solid error handling, and
informative diagnostics that told you what was going on even if things
are going fine? Working with sqlite3 and achieving these goals is quite
a challenge. Well, it was, anyway. I present to you my aa_sqlite.py
library, a toolkit I wrote to address precisely these issues.

## Documentation

Documentation is inside `aa_sqlite.py`.

## Examples

Examples are inside `aa_sqlite.py`, at the end of the file. You can run
them this way:

    python aa_sqlite.py

## editdb.py

If you're using SqLite with Python, likely there will be times when you
want to just get in there and _mess_ with a database. Rather than write a
specific Python program to do that, perhaps my
[editdb.py](https://github.com/fyngyrz/editdb) project will do what you
need. It uses this library.
