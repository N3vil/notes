## Create an alias called 'cleanfile' that will print all lines from a file that is not a comment or is an empty line

<details>
<summary>Solution</summary>

```bash
alias cleanfile="sed -E '/^\s*(#|$)/d'"

# using grep
alias cleanfile="grep -vE '^\s*(#|$)'"
```

</details>
