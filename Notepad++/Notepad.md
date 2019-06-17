
> Written with [StackEdit](https://stackedit.io/).

### Add to the end of every line
Let's say we want to add at the end of every line this `);`.

Use `Ctrl` + `H` to open the Replace page. Then use `Regular expressions` and put:

- Find what: `$`
- Replace with: `\);`

### Add to the beginning of every line
Let's say we want to add at the end of every line this `Data_`.

Use `Ctrl` + `H` to open the Replace page. Then use `Regular expressions` and put:

- Find what: `^`
- Replace with: `Data_`

### How to convert from a row to column and from column to row

- From column to row: `CTRL` + `A` selects all. Then `CTRL` + `J` aligns them in a row.
- Fro row to column: Go to Search, Find, Replace. Find `(.)`, Replace `$1\n`, SearchMode: `Regular Expression`, Direction `Down`.

### How to remove blank lines in a file

We can use the Find and Replace option with  regular  express to remove empty lines  
  
1. Press Ctrl + F to open Find  dialog, move to Replace tab  
2. Change the  **Search Mode**  as  **Extended (\n,\r,\t,\0,\x ...)**  
3. Now,  
  
Find : `\r\n`

Replace with blank

#### [How to add single quote “ ' ”at beginning and end of field?](https://stackoverflow.com/questions/34900052/how-to-add-single-quote-at-beginning-and-end-of-field)

If all fields are ALWAYS containing alphanum and dash, you can do:

Ctrl+H

Find what:  `([\w-]+)`  
Replace with:  `'$1'`

Then click on  Replace all

`([\w-]+)`  is a character class that matches alphanumeric character (including underscore) and dash.  
This will replace each field by the same with single quotes arround it.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3NzkwNzQxNywxMzQ1NzMwOTkzLC00Mz
cxNjQ2NjMsLTEzMjY3OTY0NzUsNTE1NzE0NzRdfQ==
-->