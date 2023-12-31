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

<details>
<summary>Insert a line at the beginning of a file using sed</summary>

```bash
# sample file
$ sed '' script01.sh
echo "yes"

# test
$ sed '1i #!/bin/bash' script01.sh
#!/bin/bash
echo "yes"

# do an inplace edit with -i
$ sed -i '1i #!/bin/bash' script01.sh

$ sed '' script01.sh
#!/bin/bash
echo "yes"
```   
</details>

<details>
<summary>Append a line at the end of file using sed</summary>

```bash
sudo sed -i '$a 8.8.8.8 google.com' /etc/hosts
```   

_Note: We cannot use sudo with redirection_

```bash
sudo echo '8.8.8.8 google' >> /etc/hosts
-bash: /etc/hosts: Permission denied
```
</details>

<details>
<summary>Delete the last line of a file</summary>

```bash
sed -i '$d' script01.sh

cat script01.sh
#!/bin/bash
```
</details>


<details>
<summary>Print all lines in a file that do not start with a comment or is an empty line</summary>

```bash
sed -E '/^\s*(#|$)/d' /etc/services
```
</details>


<details>
<summary>From the sample apache config below, print only the lines between each VirtualHost block

```
# Ensure that Apache listens on port 80
Listen 80
<VirtualHost *:80>
    DocumentRoot "/www/example1"
    ServerName www.example.com

    # Other directives here
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot "/www/example2"
    ServerName www.example.org

    # Other directives here
</VirtualHost>
```
</summary>

```bash
# We can pass a range of regular expression as we would pass a range of lines
sed -n '/<VirtualHost/,/<\/VirtualHost/p' vhost.sample
```   
</details>

<details>
<summary>Without using an enhanced regular expression, print all lines in a file that do not start with a comment or is an empty line</summary>


```bash
# We can pass multiple sed expressions with a semicolon
sed '/^\s*$/d;/^\s*#/d' /etc/services
```

_The expressions can also be stored in a **sed script** and passed as an argument to the sed command_

```bash
sed -f test.sed /etc/services
```

where test.sed contains
```
/^\s*$/d
/^\s*#/d
```

</details>