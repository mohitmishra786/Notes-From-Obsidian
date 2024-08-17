Whatever we will be discussing below is very generic and it applies for both Relational or Non-Relational databases.

## Vertical Scaling
- Adding more **CPU, RAM, Disk** to the database
- Requires downtime during reboot
- this gives us power to handle move load, which is exactly what we call as scale
- But keep in mind this has itas physical limitation.

## Horizontal Scaling
- basically when read is much more then write something like 90:10 ratio.
- we can move reads to some other database so that "master" is free to do writes. 
- All servers should know which database object to connect to get things done.