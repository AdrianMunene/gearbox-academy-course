---
title: "Embedded Systems, Integrated Development Environments (IDEs), Code Publishing"
nav_order: 3
---
[Home](index.md)

## Introduction to Embedded Systems
Embedded systems are specialized computing devices designed for specific tasks. They typically consist of:
- **Microcontrollers (MCUs)**: Small computers on a single chip (e.g., ESP32, Raspberry Pi Pico).
- **Firmware**: Low-level software controlling hardware behaviour.
- **Peripherals**: Sensors, actuators, and communication modules.

## Introduction to IDEs (Thonny, Arduino, Pico C/C++ SDK)
IDEs (Integrated Development Environments) simplify programming for embedded systems:

- **Thonny**  
  - Beginner-friendly Python IDE for microcontrollers.  
  - Features an intuitive interface with built-in debugging tools.  
  - Suitable for Raspberry Pi Pico and other Python-based development boards.  

- **Arduino IDE**  
  - Provides an easy-to-use interface for writing, compiling, and uploading code.  
  - Supports C++ programming and a large library of pre-built functions.  
  - Compatible with various microcontrollers, including Arduino boards and ESP32.  

- **Pico C/C++ SDK**  
  - A software development kit for programming the Raspberry Pi Pico in C/C++.  
  - Includes low-level access to hardware features like GPIO, SPI, and I2C.  
  - Enables more efficient and optimized firmware development for embedded systems.  

## Introduction to C and Embedded C

### Introduction to C
C is a general purpose programming language commonly used on computer architectures that range from the largest supercomputers to the smallest microcontrollers and embedded systems.

C is widely used in embedded systems due to its efficiency and hardware-level access. Key concepts:

#### Pointers
Pointers store memory addresses instead of actual values, allowing efficient memory management.

```c
#include <stdio.h>

int main() {
    int num = 10;
    int *ptr = &num;

    printf("Value of num: %d\n", num);
    printf("Address of num: %p\n", &num);
    printf("Value stored in pointer: %p\n", ptr);
    printf("Value pointed by pointer: %d\n", *ptr);

    return 0;
}
```

#### Arrays
Arrays store multiple values of the same data type in contiguous memory locations.

```c
#include <stdio.h>

int main() {
    int numbers[] = {10, 20, 30, 40, 50};

	//Accessing the first element in an array
	printf("%d", numbers[0])

    for(int i = 0; i < 5; i++) {
        printf("Element %d: %d\n", i, numbers[i]);
    }

    return 0;
}
```

#### Recursion
Recursion is a technique where a function calls itself to solve a problem.

```c
#include <stdio.h>

int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}

int main() {
    int num = 5;
    printf("Factorial of %d is %d\n", num, factorial(num));
    return 0;
}
```

#### C-Style Object-Oriented Programming (OOP) Using Structs and Typedef
C does not have built-in OOP support like C++ but can achieve similar principles using **structs** and **typedef**.

Example: **Defining a structure and using it like an object**
```c
#include <stdio.h>

typedef struct {
    char name[50];
    int age;
} Person;

void displayPerson(Person p) {
    printf("Name: %s\n", p.name);
    printf("Age: %d\n", p.age);
}

int main() {
    Person person1 = {"John Doe", 25};
    displayPerson(person1);
    return 0;
}
```

Example: **Using function pointers in a struct (polymorphism-like behaviour)**
```c
#include <stdio.h>

typedef struct {
    void (*speak)();
} Animal;

void dogSpeak() {
    printf("Woof! Woof!\n");
}

void catSpeak() {
    printf("Meow! Meow!\n");
}

int main() {
    Animal dog, cat;
    dog.speak = dogSpeak;
    cat.speak = catSpeak;

    dog.speak();
    cat.speak();

    return 0;
}
```

### Introduction to Embedded C
Embedded C extends standard C by incorporating additional features for hardware-level programming. It is used to write firmware for microcontrollers and provides direct access to hardware components such as registers, I/O ports, and interrupts.

#### Differences Between C and Embedded C

| Feature      | C Programming               | Embedded C Programming                           |
| ------------ | --------------------------- | ------------------------------------------------ |
| Platform     | General-purpose computers   | Microcontrollers & embedded systems              |
| Memory Usage | Uses standard memory models | Optimized for low memory environments            |
| Libraries    | Standard C libraries        | Hardware-specific libraries (e.g., GPIO, timers) |
| Execution    | Runs on OS                  | Runs on bare-metal hardware                      |
| Portability  | Highly portable             | Often hardware-specific                          |

## Code Publishing - GitHub
To publish embedded system projects on GitHub:
1. Write code in the chosen IDE.
2. Use `git init` to initialize a repository.
3. Commit changes and push to GitHub.
4. Include a README.md file with project details.
5. Share the repository link for collaboration.

## Takeaway
Understanding embedded systems is crucial for developing efficient embedded programs. Microcontrollers like the ESP32 and Raspberry Pi Pico serve as the foundation for embedded applications, while IDEs such as Thonny, Arduino IDE, and the Pico C/C++ SDK streamline the development process.

Programming in C provides direct hardware control, making it ideal for resource-constrained environments. Embedded C enhances standard C by integrating low-level hardware control, making it indispensable for embedded systems development. Mastering GitHub for version control ensures proper documentation, collaboration, and project management in embedded development.