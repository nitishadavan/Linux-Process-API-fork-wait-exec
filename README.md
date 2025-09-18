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
include <stdio.h>
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
	return 0; }

```
##OUTPUT

<img width="584" height="146" alt="Screenshot 2025-09-18 141706" src="https://github.com/user-attachments/assets/3eccd8c1-8934-4e1f-adea-cb59de4cf32b" />







```
## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>

int main() {
    int pid;
    pid = fork();

    if (pid == 0) {
        printf("I am child, my pid is: %d\n", getpid());
        printf("My parent pid is: %d\n", getppid());
        exit(0);
    } else {
        printf("I am parent, my pid is: %d\n", getpid());
        sleep(100);
        exit(0);
    }
}
```
##OUTPUT

<img width="329" height="179" alt="Screenshot 2025-09-18 141734" src="https://github.com/user-attachments/assets/b3600956-6e8f-4e7d-ae66-03805e01c0b6" />

3.
```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```
 OUTPUT:

<img width="675" height="826" alt="Screenshot 2025-09-18 141755" src="https://github.com/user-attachments/assets/cdadb153-feda-4b86-bfe5-41d692aaff42" />

 <img width="574" height="1022" alt="Screenshot 2025-09-18 141824" src="https://github.com/user-attachments/assets/6b04ef3a-f263-4bc4-8b9e-3530d67f6601" />

 <img width="1885" height="1026" alt="Screenshot 2025-09-18 141838" src="https://github.com/user-attachments/assets/66c784f3-967e-44a9-a18c-56cef64f82af" />

<img width="1919" height="746" alt="Screenshot 2025-09-18 141851" src="https://github.com/user-attachments/assets/27560380-6111-45ba-8b7e-e97b66115b18" />


        
        















# RESULT:
The programs are executed successfully.
