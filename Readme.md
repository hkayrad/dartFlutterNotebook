# [hkayrad](https://www.github.com/hkayrad/)'s [<img src="./img/dart.png" width="24"> Dart](https://dart.dev) and [<img src="./img/flutter.png" width="24"> Flutter](https://flutter.dev) Notebook

## Table of Contents
1. [Links](#links)
2. [Dart](#dart)
   1. [Print](#1.-print)
   2. [Variable Types](#2.-variable-types)
      * [Single Value Varibles](#single-value-variables)
      * [Lists](#lists)
   3. [Functions](#3.-functions)
   4. [Classes](#4.classes)
      * [Contstructor](#constructor)
      * [Inheritence](#inheritence)
<br></br>

## Links
1. [<img src="./img/falcon.png" width="24"> <span style="font-size:24px">Author's Website</span>](https://hkayrad.me)
2. [<img src="./img/dart.png" width="24"> <span style="font-size:24px">Dart Website</span>](https://dart.dev/)
   * [<img src="./img/dart.png" width="20"> <span style="font-size:20px">Dart Documentation</span>](https://dart.dev/guides)

## Dart

### **1. Print**
Printing something to command line is the most basic thing you must know so you can print things like errors, values, debug codes.

```
void main() {
    print('Hakan'); // Prints Hakan to the command line.
}
```

### **2. Variable Types**
Dart is a statically typed language. Which means you have to specify variable types.

#### **Single Value Variables**
```
void main() {
    int age = 30; // integer
    String name = 'Hakan'; // string
    bool isDartHard = false; // boolean
}
```
There is also a type called **'dynamic'** which you can change it's type after declaring it.
```
void main() {
    dynamic test = 'Hakan' // dynamic
    test = 30;
    test = true;
}
```

#### **Lists**
You create lists by typing **'List'** first and **[ ]** after the equal sign.
```
void main() {
    List names = ['mario', 'luigi', 'yoshi'];
    print(names); // Prints the whole list like [mario, luigi, yoshi]
}
```

You can use functions to add or remove something to the list. Also you can add strings, integers and booleans to the same list **if you didn't specify the type of the list**.

_names.add()_
```
void main() {
    List names = ['mario', 'luigi', 'yoshi'];
    names.add('bowser');
    print(names); // Prints [mario, luigi, yoshi, bowser]

    names.add(30);
    names.add(true); // These don't spit out errors.
}
```

_names.remove()_
```
void main() {
    List names = ['mario', 'luigi', 'yoshi', 30];
    names.remove('yoshi');
    print(names); // Prints [mario, luigi, 30]
    names.remove(30);
    print(names); // Prints [mario, luigi]
```

_Specify List Type_
```
void main() {
    List<String> names = ['mario', 'luigi', 'yoshi'];
    names.add(30); // This would give error because you can't assign integer to String typed list.
}
```

### **3. Functions**
You have to specify what type of item you are returning from the function.
>main() is the top level required function of dart. It'll get executed automatically when program starts.
```
int getAge() {
    return 30;
}

String getName() {
    return 'Hakan';
}

void main() {
    age = getAge();
    name = getName();
}
```
>**You can make arrow funtions like JavaScript**
```
int getAge() => 30;

String getName() => 'Hakan';

void main() {
    age = getAge();
    name = getName();
}
```
They both have the same functionality but bottom one is neater.

### **4. Classes**

**Classes for Starters**

Classes are blueprints for objects. We use classes to describe these objects by giving them properties and methods. Metods are just functions.

```
void main() {
    User userOne = User(); // User is the type of userOne

    print(userOne.username); // Will print out Hakan
    print(userOne.age); // Will print out 17
    userOne.login(); // Will call login() function inside the User class and execute lines inside of it. Which is print('User logged in');

    User userTwo = User(); // User is the type of userTwo
    print(userTwo.username); // This is also Hakan but userTwo may want it's name to be different. So we use constructors.
}

class User {
    String username = 'Hakan';
    int age = 17;

    void login() {
        print('User logged in');
    }
}
```

#### **Constructor**
Constructor is a special function that has to have the same name as the class and you don't specify the type of the function.
```
void main() {
    User userOne = User('Hakan', 17);
    User userTwo = User('Kayra', 30);
    print(userOne.username); // Will print out Hakan
    print(userTwo.username); // Will print out Kayra
    print(userOne.age); // Will print out 17
    print(userTwo.age); // Will print out 30
}

class User {
    String username;
    int age;

    User(String username, int age) {
        this.username = username;
        this.age = age;
        // 'this' refers to the instance we created using `User variableName = User('name', age);`
    }  

    void login() {
        print('User logged in');
    }
}
```

#### **Inheritence**
Let's say we have a class called SuperUser and we want it to have same extra properties/methods but also have the properties/methods of User class.

```
void main() {
    User userOne = User('Hakan', 17);
    SuperUser admin = SuperUser('Admin', 23);

    print(userOne.username); // Will print out Hakan
    print(admin.username); // Will print out Admin

    admin.login(); // Will call login()
    admin.publish(); // Will call publish()

    userOne.login(); // Will call login()
    userOne.publish(); // Will throw error beacuse User class doesn't have publish() function
}

class User {
    String username;
    int age;

    User(String username, int age) {
        this.username = username;
        this.age = age;
        // 'this' refers to the instance we created using `User variableName = User('name', age);`
    }  

    void login() {
        print('User logged in');
    }
}

class SuperUser extends User { // Extends means it inherits from User class

    // We need constructor for SuperUser but we can inherit it from User class too.

    SuperUser(String username, int age) : super(username, age); 
    
    // super() function calls User class' constructor and appies it in SuperUser class because both User and SuperUser are users and have the same basic data.

    void publish() {
        print('Published'); // SuperUser only method.
    }
}
```