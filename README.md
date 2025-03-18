# Studio-6---Parsing-String
Name: (Kwabena Adjei Omanhene Gyimah)
Q2: 
#include <stdio.h>

int main() {
    char input_string[100];
    
    printf("Enter input: ");
    fgets(input_string, sizeof(input_string), stdin);
    
    printf("%s\n", input_string);
    return 0;
}

output: Enter input: Hello, world!
Hello, world!

Q3: Difference Between Initial and Subsequent Calls to strtok()

The initial call to strtok() requires the string to be tokenized as its first argument. Subsequent calls should pass NULL instead, allowing strtok() to continue parsing from where it left off.

Q4:
Suitable Delimiter for Regular Text Input

A space character (" ") should be used as the delimiter for regular text input.

Q5: #include <stdio.h>
#include <string.h>

int main() {
    char input_string[100];

    printf("Enter input: ");
    fgets(input_string, sizeof(input_string), stdin);
    
    char *token = strtok(input_string, " ");
    printf("%s\n", token);
    
    return 0;
}

output: Enter input: Hello world
Hello

Q6)
#include <stdio.h>
#include <string.h>

int main() {
    char input_string[100];

    printf("Enter input: ");
    fgets(input_string, sizeof(input_string), stdin);

    char *token = strtok(input_string, " ");
    while (token != NULL) {
        printf("%s\n", token);
        token = strtok(NULL, " ");
    }

    return 0;
}

output: Enter input: This is an input string.
This
is
an
input
string.

Q7: input_string[strcspn(input_string, "\n")] = '\0';

Q8:
int max_args = 15;
int max_argv_size = max_args + 2; // one for argv[0], one for null terminator
char* cmd;
char* my_argv[max_argv_size];

Q9:
cmd = strtok(input_string, " ");
my_argv[0] = cmd;

int i = 1;
char *res;
while ((res = strtok(NULL, " ")) != NULL) {
    my_argv[i] = res;
    i++;
}

my_argv[i] = NULL; // Null-terminate the array

Q10:
#include <stdio.h>
#include <string.h>
#include <unistd.h>

int main() {
    char input_string[100];
    int max_args = 15;
    int max_argv_size = max_args + 2;
    char* cmd;
    char* my_argv[max_argv_size];

    printf("Enter command: ");
    fgets(input_string, sizeof(input_string), stdin);

    // Strip newline
    input_string[strcspn(input_string, "\n")] = '\0';

    // Parse command
    cmd = strtok(input_string, " ");
    my_argv[0] = cmd;

    int i = 1;
    char *res;
    while ((res = strtok(NULL, " ")) != NULL) {
        my_argv[i] = res;
        i++;
    }
    my_argv[i] = NULL; // Null-terminate

    // Execute command
    execvp(cmd, my_argv);

    // If execvp fails
    perror("execvp failed");
    return 1;
}

output: Enter command: ls -l
(total output of "ls -l" command appears here)

