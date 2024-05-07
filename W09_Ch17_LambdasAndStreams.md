# Java | Lambdas and  Streams

### Topic Notes;

## 1. Fig17_03_StreamReduce

### Example Notes;

* A stream pipeline typically begins with a method call that creates the stream (known as the data source)

* In the following example that is achieved with rangeClosed(start, end) is from the IntStream class and it returns a sequentially ordered IntStream from the start to end values (inclusive). o, the line above will create an ordered sequence of int elements: 1,2,3,4,5,6,7,8,9,10

* The sum() method returns the sum of all the ints in the stream. This processing step is called reduction (it reduces the stream to a single value)

* A terminal operation initiates a stream pipeline’s processing and produces a result. IntStream’s sum() method is a terminal operation.

```
package javachapter17;  
import java.util.stream.IntStream;  // Imports the IntStream class for creating streams of ints

public class Fig17_03_StreamReduce {
    public static void main(String[] args) {
        System.out.printf("Sum of 1 through 10 is: %d%n",
                IntStream.rangeClosed(1, 10) // IntStream.rangeClosed(1, 10) generates a stream of integers from 1 to 10, inclusive
                         .sum()); // The sum() method calculates and returns the sum of all elements in the stream.
    }
}
```

![picture](./Images/Fig17_03_StreamReduce.png)


## 2. Fig17_04_StreamMapReduce

```
package javachapter17;
import java.util.stream.IntStream;  // Imports the IntStream class for creating streams of ints

public class Fig17_04_StreamMapReduce {
    public static void main(String[] args) {

        System.out.printf("Sum of the even ints from 2 through 20 is: %d%n",
                IntStream.rangeClosed(1, 10) // Generates a stream of integers from 1 to 10, inclusive
                         .map((int x) -> x * 2) // The map operation transforms each element of the stream by 
                                                // multiplying it by 2. This converts the range 1..10 to the even numbers 2..20
                         .sum());
    }
}
```

![picture](./Images/Fig17_04_StreamMapReduce.png)

## 3. Fig17_07_StreamFilterMapReduce

```
package javachapter17;

// Fig. 17.7: StreamFilterMapReduce.java
// Triple the even ints from 2 through 10 then sum them with IntStream.
import java.util.stream.IntStream;

public class Fig17_07_StreamFilterMapReduce {
    public static void main(String[] args) {
        System.out.printf(
                "Sum of the triples of the even ints from 2 through 10 is: %d%n",
                IntStream.rangeClosed(1, 10) // Generates a stream of integers from 1 to 10, inclusive
                         .filter(x -> x % 2 == 0) // Excludes all odd numbers, leaving only even numbers
                         .map(x -> x * 3) // Triples each element in the filtered stream
                         .sum()); // Calculates and returns the sum of all transformed stream elements
    }
}
```

![picture](./Images/Fig17_07_StreamFilterMapReduce.png)

## 4. Fig17_08_RandomIntegers

```
package javachapter17;

// Fig. 17.8: RandomIntegers.java
// Shifted and scaled random integers.
import java.security.SecureRandom;
import java.util.stream.Collectors;

public class Fig17_08_RandomIntegers {

    public static void main(String[] args) {
        SecureRandom randomNumbers = new SecureRandom(); // Creates an instance of SecureRandom

        System.out.println("Random numbers on separate lines:");
        randomNumbers.ints(10, 1, 7) // Generates 10 random integers between 1 and 6 (inclusive)
                     .forEach(System.out::println); // System.out::println is a method reference, a shortcut for a lambda calling
                                                    // It means that the println method of the System.out object will be called.
                                                    // The compiler converts "System.out::println" to "x->System.out.println(x)"
                                                    // x represents the current stream element

        // Display 10 random integers on the same line
        String numbers = randomNumbers.ints(10, 1, 7) // Generates another set of 10 random integers between 1 and 6
                                      .mapToObj(String::valueOf) // Transforms each integer into its String form, creating a new stream of Strings. 
                                                                 // This is different from the previous map operation(.map(x -> x * 3)), which returned an IntStream. 
                                                                 // Here, mapToObj enables mapping from integers to a stream of reference-type elements.
                                                                 // The compiler converts "String::valueOf" to "x -> String.valueOf(x)"
                                                                 // This lambda function calls valueOf for each integer, converting its String representation.
                                      
                                      .collect(Collectors.joining(" ")); // Concatenate all the Strings with “ “ between each one.
                                                                         // Method collect is a form of reduction because it returns one object (a String)
        /*
            Step-by-Step Execution:
                .ints(...)   : Generate Integers   : [5, 3, 2, 6, 1, 4, 5, 3, 2, 6].
                .mapToObj(..): Map to Strings      : ["5", "3", "2", "6", "1", "4", "5", "3", "2", "6"].
                .collect(
                    Collectors.joining(" "))       : Combine Strings with Spaces : "5 3 2 6 1 4 5 3 2 6".
        */

        System.out.printf("%nRandom numbers on one line: %s%n", numbers); // Prints the concatenated string of numbers
    }
}
```

![picture](./Images/Fig17_08_RandomIntegers.png)

## 5. Fig17_09_IntStreamOperations

```

```

## 6. Fig17_11_ArraysAndStreams

```

```

## 7. Fig17_12_ArraysAndStreams2

```

```

## 8. Fig17_13_Employee

```

```

## 9. Fig17_14_ProcessingEmployees

```

```

## 10. Fig17_22_StreamOfLines

```

```

## 11. Fig17_24_RandomIntStream

```

```
