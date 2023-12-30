## sed

### Stream Editor for programatically editing files

<details>
<summary>Print all lines in a file using sed</summary>

```bash
sed '' /etc/services
```   
</details>

<details>
<summary>Print the first and the last line of a file using sed</summary>

```bash
sed -n '1p' /etc/services

sed -n '$p' /etc/services
```   
</details>

<details>
<summary>Why does sed print lines twice? How do you prevent it?</summary>

Sed will automatically print all the lines it has read. To suppress this behaviour use the -n option.

</details>

<details>
<summary>How is sed better than head and tail command?</summary>

sed can print any range of lines whereas head and tail commands only print from the beginning and till the end of the file. 

```bash
sed -n '10,15p' /etc/services

sed -n '20,$p' /etc/services
```   
</details>