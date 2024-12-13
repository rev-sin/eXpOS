
1. to load a file into XSM disk

```
$ cd $HOME/myexpos/xfs-interface
$ ./xfs-interface
# load --data $HOME/myexpos/sample.dat
```

3. to copy the entries from a specific block of the loaded file, here for instance, blocks 3 4 is where inode_table contents can be found
````
# copy 3 4 $HOME/myexpos/inode_table.txt
````
4. instead you can also use dump to generate files ie, inode table to the xfs-interface directory

`dump --inodeusertable`

5. copy the data blocks

`# copy 69 69 $HOME/myexpos/data.txt`