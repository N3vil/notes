### Write a script that will look for all scripts under a directory and add shebang line only if it is missing

<details>

<summary>Solution</summary>

```bash
#!/bin/bash

#fix-shebang.sh

if [[ ! -d $1 ]]; then
  echo "Invalid Argument. $1 is not a directory"
  exit 1  
fi

scripts=`ls -1 $1/*.sh`

for script in $scripts; do
  echo "Script file: $script"
  firstline=$(sed -n '1p' $script)

  if [[ $firstline != "#!"* ]]; then      
    echo "Inserting a shebang line to $script"  
    sed -i '1i #!/bin/bash' $script
  fi      

done
```

</details>