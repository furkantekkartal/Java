# Java | All java codes in the learning process

## 1. General Codes

* Trial

### Printf commands;

```
public class PrintfExample {
    public static void main(String[] args) {
        String name = "John Doe";
        int age = 25;
        double salary = 5000.75;
        boolean isEmployed = true;
        char grade = 'A';

        // Using printf with different variable types
        System.out.printf("Name: %s, Age: %d, Salary: $%.2f, Employed: %b, Grade: %c%n", name, age, salary, isEmployed, grade);
    }
}
```

### for loop;
```
import java.util.LinkedList;
import java.util.List;

public class ForExample {
    public static void main(String[] args) {

        int[] numbers = {10, 20, 30, 40, 50};
        List<Integer> numLists = new LinkedList<>();

        // For type 1
        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }

        // For type 2
        for (int i : numbers) {
            numLists.add(i);
        }
        System.out.println(numLists);
    }
}
```
```
public class ListTest {

    public static void main(String[] args) {
        // add colors elements to list1
        String[] colors = {"black", "yellow", "green", "blue", "violet", "silver"};
        List<String> list1 = new LinkedList<>();



        System.out.println(list1);
    }
}
```


### if commands;
```
public class IfExample {
    public static void main(String[] args) {
        int x = 10;

        // One-line if statement
        String message = (x > 5) ? "x is greater than 5" : "x is not greater than 5";
        System.out.println(message);

        // if statement
        if (x > 5) {
            System.out.println("x is greater than 5");
        } else if (x < 5) {
            System.out.println("x is less than 5");
        } else {
            System.out.println("x is equal to 5");
        }
    }
}
```


### Decleration of variables, array, arraylist, object;

```
public class MyVariables {
    public static void main(String[] args) {

        int age = 10; // You are 10 years old!
        long bigNumber = 1234567890; // A really big number
        double pi = 3.14159; // Pi, used for circles
        float smallDecimal = 2.5f; // A smaller decimal number
        char initial = 'A'; // Your first initial
        String name = "Alice"; // Your name
        boolean isHappy = true; // Are you happy?

        int[] scores = {90, 85, 95}; // Arrays (like a list of things)

        // ArrayList (like a flexible list)
        ArrayList<String> colors = new ArrayList<>(); // A flexible list that can grow or shrink (like a list of colors).
            colors.add("red");
            colors.add("blue");

        // Objects (like a toy with properties)
        class Toy {
            String color;
            int size;
        }
        Toy teddy = new Toy();
            teddy.color = "brown";
            teddy.size = 20; // 20 cm tall
    }
}
```

### toString command;

```
public String toString() {
        return String.format(
                "MyVariables: \n" +
                "age: %d\n" + 
                "bigNumber: %d\n" + 
                "pi: %.2f\n" + 
                "smallDecimal: %.2f\n" + 
                "initial: %c\n" + 
                "name: %s\n" + 
                "isHappy: %b\n" + 
                "scores: %s\n" + 
                "fruits: %s", 
                age, bigNumber, pi, smallDecimal, initial, name, isHappy, 
                Arrays.toString(scores), fruits.toString() // Assuming you have a 'fruits' ArrayList
        );
}


```

### Inheritance example;

```
public class InheritanceExample {
    public static void main(String[] args) {

        Frog frog1 = new Frog("Green");
        Cat cat1 = new Cat("Yellow");

        cat1.move();
        frog1.move();

        System.out.printf("Cat 1 color: %s %s%n", cat1.color, cat1.move()); 
        System.out.printf("Frog 1 color: %s %s%n", frog1.color, frog1.move());
    }
}

class Animal {
    protected String color;

    public Animal(String color) {
        this.color = color;
    }
        
    @Override
    public String toString() {
        return "Color: " + color;
    }
}


class Frog extends Animal {
    protected String movement;

    public Frog(String color) {
        super(color);
    }

    public String move() { // Changed return type to String
         movement = "Frogs jump"; 
         return movement;
    }
}

class Cat extends Animal {
    protected String movement;

    public Cat(String color) {
        super(color);
    }

    public String move() { // Changed return type to String
        movement = "Cats walk."; 
        return movement;
    }
}

```

### Interface example;
```
public class InterfaceExample {
    public static void main(String[] args) {
        // Creating instances of classes implementing the interface
        Dog dog = new Dog("Brown");
        Cat cat = new Cat("White");

        // Calling methods from the interface
        System.out.printf("Dog: %s%n", dog);
        dog.makeSound();
        dog.move();

        System.out.printf("Cat: %s%n", cat);
        cat.makeSound();
        cat.move();
    }
}

// Animal interface
interface Animal {
    void makeSound();
    void move();
}

// Dog class implementing Animal interface
class Dog implements Animal {
    private String color;

    public Dog(String color) {
        this.color = color;
    }

    @Override
    public void makeSound() {
        System.out.println("Dog barks.");
    }

    @Override
    public void move() {
        System.out.println("Dog runs.");
    }

    @Override
    public String toString() {
        return "Color: " + color;
    }
}

// Cat class implementing Animal interface
class Cat implements Animal {
    private String color;

    public Cat(String color) {
        this.color = color;
    }

    @Override
    public void makeSound() {
        System.out.println("Cat meows.");
    }

    @Override
    public void move() {
        System.out.println("Cat walks.");
    }

    @Override
    public String toString() {
        return "Color: " + color;
    }
}

```

### Generics example;
https://www.youtube.com/watch?v=K1iu1kXkVoA&t=920s
```
// Fig. 16.2: CollectionTest.java
// Collection interface demonstrated via an ArrayList object.
import java.util.List;
import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

public class CollectionTest
{
   public static void main(String[] args)
   {
      // add elements in colors array to list
      String[] colors = {"MAGENTA", "RED", "WHITE", "BLUE", "CYAN"};
      List<String> list = new ArrayList<>();

      for (String color : colors)
         list.add(color); // adds color to end of list

      // add elements in removeColors array to removeList
      String[] removeColors = {"RED", "WHITE", "BLUE"};
      List<String> removeList = new ArrayList<>();

      for (String color : removeColors)
         removeList.add(color);

      // output list contents
      System.out.println("ArrayList: ");

      for (int count = 0; count < list.size(); count++)
         System.out.printf("%s ", list.get(count));

      // remove from list the colors contained in removeList
      removeColors(list, removeList);

      // output list contents
      System.out.printf("%n%nArrayList after calling removeColors:%n");

      for (String color : list)
         System.out.printf("%s ", color);
   }

   // remove colors specified in collection2 from collection1
   private static void removeColors(Collection<String> collection1,
      Collection<String> collection2)
   {
      // get iterator
      Iterator<String> iterator = collection1.iterator();

      // loop while collection has items
      while (iterator.hasNext())
      {
         if (collection2.contains(iterator.next()))
            iterator.remove(); // remove current element
      }
   }
} // end class CollectionTest
```

### Iterator example;
https://www.youtube.com/watch?v=G3uNYHtn83c&list=PL59LTecnGM1NRUyune3SxzZlYpZezK-oQ&index=68
```
import java.util.ArrayList;
import java.util.Iterator;

public class NewClass1 {
    public static void main(String[] args){
               
        ArrayList<String> foods = new ArrayList<>();
        foods.add("Pizza");
        foods.add("Hamburger");
        foods.add("Pasta");
        foods.add("Kebap");
        
        System.out.println(foods);
        
        Iterator<String> it = foods.iterator();
        
        while (it.hasNext()){
            if(it.next() == "Hamburger"){
                it.remove();
            }
        }
        System.out.println(foods);        
    }
}
```
