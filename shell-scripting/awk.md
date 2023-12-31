## awk

### awk is a reporting tool 

<details>
<summary>What are the different blocks in an awk script/expression?</summary>

**BEGIN** for printing headers, **MAIN** for printing fields, **END** for printing summary

Here is what an awk expression looks like...
```
BEGIN { stmt1;stmt2...} { stmt1;stmt2...} END { stmt1;stmt2...}
```

_Note how the MAIN block begins without any keyword_

</details>

<details>
<summary>print all the lines in a file using awk</summary>

```bash
awk '{ print }' /etc/passwd
```   
</details>

<details>
<summary>From /etc/passwd print all the lines that end with a bin/bash </summary>

```bash
# Note similarity between the sed and awk expression
awk '/bin\/bash$/{ print }' /etc/passwd
```   
</details>


<details>
<summary>print the contents of /etc/passwd in the following format

```
 NUM            USERNAME   UID
   1                root     0
   2              daemon     1
   3                 bin     2
   4                 sys     3
   5                sync     4
   6               games     5
   7                 man     6
 ...
```
</summary>

```bash
# using the built-in NR variable 
awk 'BEGIN {FS=":"; printf "%4s%20s%6s\n","NUM","USERNAME","UID"} { printf "%4d%20s%6s\n",NR,$1,$3 }' /etc/passwd

# using custom variable
awk 'BEGIN {FS=":"; printf "%4s%20s%6s\n","NUM","USERNAME","UID"; COUNT=0 } { COUNT++; printf "%4d%20s%6s\n",COUNT,$1,$3 }' /etc/passwd
```   
</details>

<details>
<summary>Print Username, UserID of users from /etc/passwd that use a bash shell. Also print a summary of total users and the number of users which use bash shell.</summary>

```bash
awk 'BEGIN {FS=":"; COUNT=0; printf "%4s%20s%6s\n","NUM","USERNAME","UID"}  /bash$/{ COUNT++; printf "%4s%20s%6s\n",COUNT,$1,$3 } END{ print "There are " NR " users of which, " COUNT " uses bash"}' /etc/passwd
```

```
 NUM            USERNAME   UID
   1                root     0
   2              ubuntu  1000
There are 28 users of which, 2 uses bash
```
</details>

<details>
<summary>Try solving the above problem using an awk script file</summary>

```bash
awk -f test.awk /etc/passwd
```   

test.awk 
```
# BEGIN BLOCK
BEGIN {
    FS=":";
    COUNT=0;
    printf "%4s%20s%6s\n","NUM","USERNAME","UID"
} 

# MAIN BLOCK
/bash$/ { 
    COUNT++;
    printf "%4s%20s%6s\n",COUNT,$1,$3
} 

# END BLOCK
END {
    print "There are " NR " users of which, " COUNT " uses bash"
}
```
</details>
