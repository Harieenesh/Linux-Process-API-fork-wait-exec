# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
      #include <stdio.h>
      #include <sys/types.h>
      #include <unistd.h>
      int main(void)
      {	//variable to store calling function's process id
      	pid_t process_id;
      	//variable to store parent function's process id
      	pid_t p_process_id;
      	//getpid() - will return process id of calling function
      	process_id = getpid();
      	//getppid() - will return process id of parent function
      	p_process_id = getppid();
      	//printing the process ids
      
      //printing the process ids
      	printf("The process id: %d\n",process_id);
      	printf("The process id of parent function: %d\n",p_process_id);
      	return 0;
        }
```
##OUTPUT

![443206347-d77b05bc-7be7-4ead-b24b-115735565bd1](https://github.com/user-attachments/assets/3950e325-a88d-443a-a7e6-6f6c5911a8d9)

## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
```
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main() {
int status;

printf("Running ps with execl\n");
if (fork() == 0) {
    execl("ps", "ps", "-f", NULL);
    perror("execl failed");
    exit(1);
}
wait(&status);

if (WIFEXITED(status)) {
    printf("Child exited with status: %d\n", WEXITSTATUS(status));
} else {
    printf("Child did not exit successfully\n");
}

printf("Running ps with execlp (without full path)\n");
if (fork() == 0) {
    execlp("ps", "ps", "-f", NULL);
    perror("execlp failed");
    exit(1);
}
wait(&status);

if (WIFEXITED(status)) {
    printf("Child exited for execlp with status: %d\n", WEXITSTATUS(status));
} else {
    printf("Child did not exit successfully\n");
}

printf("Done.\n");
return 0;
}


```

##OUTPUT

![443206388-8de504cb-0bdf-4ebe-8ee6-c014dad1f60f](https://github.com/user-attachments/assets/afa6f020-7d8f-4ffd-be80-1e0cbbc8bad7)
















# RESULT:
The programs are executed successfully.
