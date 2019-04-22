
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQzNzE2NDY2MywtMTMyNjc5NjQ3NSw1MT
U3MTQ3NF19
-->