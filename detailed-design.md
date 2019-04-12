## 2.1 - Detailed list of Linux modules that will be modified/affected
The only linux module we are going to be modifying is the scheduler `mq-deadline.c`. 


## 2.2 - Detailed list of any new modules that you will produce [or 'Not Applicable' if there are none]
Not Applicable



## 2.3 - Class diagram showing affected modules [and any new modules] and how they related to one another
[Diagram](https://github.com/aboyac/cmsi387-project/issues/1#issue-432373570)



## 2.4 - List or table of explanations of all command line options that will be implemented
| Description                                              | Command                                               |
| -------------------------------------------------------- | :---------------------------------------------------- |
| First gain root access                                   | `sudo -s`                                             |
| Use this to check what the current I/O scheduler is      | `cat /sys/block/sda/queue/scheduler`                  |
| This command changes the current scheduler to "deadline" | `sudo echo deadline > /sys/block/sda/queue/scheduler` |
