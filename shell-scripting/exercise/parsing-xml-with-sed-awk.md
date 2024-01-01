### Consider the below apache config file 

```
<VirtualHost *:80>
DocumentRoot /www/example
ServerName www.example.org
# Other directives here
</VirtualHost>
<VirtualHost *:80>
DocumentRoot /www/theurbanpenguin
ServerName www.theurbanpenguin.com
# Other directives here
</VirtualHost>
<VirtualHost *:80>
DocumentRoot /www/linuxformat
ServerName www.linuxformat.com
# Other directives here
</VirtualHost>
```

### Add a new line after each VirtualHost block to make it more readable

<details>

<summary>Solution</summary>

```bash
# this actually adds a newline that begins with a space.
sed -i '/<\/VirtualHost/a \ ' vh.conf

# this will add two newlines 
sed -i '/<\/VirtualHost/a \\n' vh.conf
```
</details>

### Print the VirtualHost record for example.com

<details>
<summary>Solution</summary>

```bash
# The built-in RS variable can be used to specify the record separator. Here we have set it to two or more newline characters. 

awk 'BEGIN {RS="\\n\\s*\\n"} /example/ { print }' vh.conf 
```

```
<VirtualHost *:80>
DocumentRoot /www/example
ServerName www.example.org
# Other directives here
</VirtualHost>
```
</details>



