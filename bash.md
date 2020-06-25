# Bash Script Cheats.


1. counting lines in a file.
~~~bash
wc -l file_name
#with pipe
cat file_name | wc -l
~~~

2. delete last line of file.
~~~bash
 | sed '$d'
~~~

3. find files. that are recorded after time, and sort them
~~~bash
find location -newermt time -type f | sort
~~~

4. Declare Bad Exit from bash.
~~~bash
 exit 1 
~~~

5. Writing function bash

~~~bash

function_name(){


}

function function_name{

  
}
~~~

6. Checking the size in linux. [ref](https://phoenixnap.com/kb/linux-check-disk-space)

Checking space untilization by directories on current level.
~~~bash
du -h -d1 .
~~~

To check disk space and utilization info.
~~~bash
// normal
df

// in megabyte and KB.
df -h
~~~

7. grep, cut, sed.

~~~bash

ls | grep "cool" | sed "s/\/d/\/#d/" | 


