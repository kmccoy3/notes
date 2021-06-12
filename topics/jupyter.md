
# Jupyter

**Keyboard Shortcuts:**
* `Shift` + `Enter` to run a cell (code or markdown)
* `a` to insert a new cell above the current cell
* `b` to insert a new cell below the current cell
* `m` to change the current cell to Markdown
* `y` to change the current cell to code
* `d` + `d` (twice) to delete the selected cells
* `c` to copy, `x` to cut, `v` to paste current cell
* `0` + `0` to restart kernel
Note: Need to hit `esc` or click to the left of cell in order to exit edit mode.

**To find runtime of cell or line:**
```Python
# to find average runtime
%timeit CODE_LINE
%%timeit CODE_CELL

# to find runtime
%time CODE_LINE
%%time CODE_CELL
```

**Other Miscellaneous Tips:**
* Use `!` prefix to run a single bash command line
  * Use `%%bash` to change entire cell to bash mode
* Add `?` before any function to retrieve documentation
* Use `%%js`, `%% html`, `%%latex`, `%%python2`, `%%python3` etc. to render code in that language.

**If you need to restart jupyter and kernel restart doesn't work, run following in terminal:**
```console
$ sudo service jupyter restart
```

**Good Resources / Further Reading:**
* https://blog.udemy.com/jupyter-notebook-shortcuts/
* https://towardsdatascience.com/jupyter-notebooks-tips-and-tricks-4e995e7b1fd0
