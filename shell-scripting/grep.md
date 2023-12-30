## grep

<details>
<summary>Count the number of lines in a file using grep?</summary>

```
grep -c '' /etc/services
```   
</details>

<details>
<summary>Print all lines in a file that do not start with a comment or is an empty line</summary>

```
grep -vE '^(#|$)' /etc/ssh/ssh_config
```
</details>

<details>
<summary>What is the use of -E option?</summary>

Used for passing Enhanced Regular Expression instead of a Basic Regular Expression

</details>
