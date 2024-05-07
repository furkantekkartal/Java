# Java | Lambdas and  Streams

## 1. IntStreamOperations

```
package javachapter17;

// Fig. 17.5: IntStreamOperations.java
// Demonstrating IntStream operations.
import java.util.stream.IntStream;

public class IntStreamOperations 
{
   public static void main(String[] args)
   {
      int[] values = {3, 10, 6, 1, 4, 8, 2, 5, 9, 7};

      // display original values
      System.out.print("Original values: ");
      IntStream.of(values)  //: It's a method in the IntStream class. Creates a stream from an array of integers.
              .forEach(value -> System.out.printf("%d ", value)); //: Iterates over each element of the stream and applies the given action.
      System.out.println(); //Output: Original values: 3 10 6 1 4 8 2 5 9 7 


      // count, min, max, sum and average of the values
      System.out.printf("%nCount: %d%n",    IntStream.of(values).count()); // 10
      System.out.printf("Min: %d%n",        IntStream.of(values).min().getAsInt()); // 1
      System.out.printf("Max: %d%n",        IntStream.of(values).max().getAsInt()); //10
      System.out.printf("Sum: %d%n",        IntStream.of(values).sum()); // 55
      System.out.printf("Average: %.2f%n",  IntStream.of(values).average().getAsDouble()); // 5.50

      // sum of values with reduce method
      System.out.printf("%nSum via reduce method: %d%n", IntStream.of(values).reduce(0, (x, y) -> x + y));
/*
        The reduce() method in this case is called with two parameters: 
              an identity value (0) and 
              a binary operator lambda (x, y) -> x + y. 

        The identity value is the starting point for the reduction and 
        the lambda defines how each pair of elements should be combined.

        Here's how the reduction process will unfold with the array:

        Initial Value (identity): 0

        First pair  :  0 + 3  = 3
        Second pair :  3 + 10 = 13
        Third pair  : 13 + 6  = 19
        Fourth pair : 19 + 1  = 20
        Fifth pair  : 20 + 4  = 24
        Sixth pair  : 24 + 8  = 32
        Seventh pair: 32 + 2  = 34
        Eighth pair : 34 + 5  = 39
        Ninth pair  : 39 + 9  = 48
        Tenth pair  : 48 + 7  = 55
*/

      // sum of squares of values with reduce method
      System.out.printf("Sum of squares via reduce method: %d%n",IntStream.of(values).reduce(0, (x, y) -> x + y * y));
/*
        This reduce() operation calculates the sum of the squares of each element in the array.

        Reduction Process Explained:
        Initial Value (identity): 0
        Operation               : (x, y) -> x + y * y 
                                where x is the accumulator (keeps the running total) 
                                and y is the current stream element.

        Step-by-Step Calculation:
        Initial State: Start with 0 (identity).
         First Element (3)  : Compute 0   + 3*3   = 0 + 9     = 9.
         Second Element (10): Compute 9   + 10*10 = 9 + 100   = 109.
         Third Element (6)  : Compute 109 + 6*6   = 109 + 36  = 145.
         Fourth Element (1) : Compute 145 + 1*1   = 145 + 1   = 146.
         Fifth Element (4)  : Compute 146 + 4*4   = 146 + 16  = 162.
         Sixth Element (8)  : Compute 162 + 8*8   = 162 + 64  = 226.
         Seventh Element (2): Compute 226 + 2*2   = 226 + 4   = 230.
         Eighth Element (5) : Compute 230 + 5*5   = 230 + 25  = 255.
         Ninth Element (9)  : Compute 255 + 9*9   = 255 + 81  = 336.
         Tenth Element (7)  : Compute 336 + 7*7   = 336 + 49  = 385.     
*/

      // product of values with reduce method
      System.out.printf("Product via reduce method: %d%n", IntStream.of(values).reduce(1, (x, y) -> x * y));
/*
          Reduction Process(.reduce(1, (x, y) -> x * y)):
      
        Initial State: Start with 1 (identity value for multiplication).
        First Element (3)   : Compute 1      * 3  = 3.
        Second Element (10) : Compute 3      * 10 = 30.
        Third Element (6)   : Compute 30     * 6  = 180.
        Fourth Element (1)  : Compute 180    * 1  = 180
        Fifth Element (4)   : Compute 180    * 4  = 720.
        Sixth Element (8)   : Compute 720    * 8  = 5760.
        Seventh Element (2) : Compute 5760   * 2  = 11520.
        Eighth Element (5)  : Compute 11520  * 5  = 57600.
        Ninth Element (9)   : Compute 57600  * 9  = 518400.
        Tenth Element (7)   : Compute 518400 * 7  = 3628800.
*/
      
      
      // even values displayed in sorted order
      System.out.printf("%nEven values displayed in sorted order: ");
      IntStream.of(values)
              .filter(value -> value % 2 == 0)
              .sorted()
              .forEach(value -> System.out.printf("%d ", value));
      System.out.println();
/*
Step-by-Step Execution
    Create Stream   : {3, 10, 6, 1, 4, 8, 2, 5, 9, 7}.
    Filter Even Nums : {10, 6, 4, 8, 2}.
    Sort Stream     : {2, 4, 6, 8, 10}.
    Print Each      : 2 4 6 8 10       
*/
      // odd values multiplied by 10 and displayed in sorted order
      System.out.printf("Odd values multiplied by 10 displayed in sorted order: ");
      IntStream.of(values)
              .filter(value -> value % 2 != 0)
              .map(value -> value * 10)
              .sorted()
              .forEach(value -> System.out.printf("%d ", value));
      System.out.println();
/*
Step-by-Step Execution
    Create Stream   : {3, 10, 6, 1, 4, 8, 2, 5, 9, 7}.
    Filter Odd Nums : {3, 1, 5, 9, 7}.
    Multiply by 10  : {30, 10, 50, 90, 70}.
    Sort Stream     : {10, 30, 50, 70, 90}.
    Print Each      : 10 30 50 70 90       
*/
      // sum range of integers from 1 to 10, exlusive
      System.out.printf("%nSum of integers from 1 to 9: %d%n",
              IntStream.range(1, 10).sum());
              // IntStream    : {3, 10, 6, 1, 4, 8, 2, 5, 9, 7}.  
              // .range(1, 10): {1, 2, 3, 4, 5, 6, 7, 8, 9}.
              // .sum()       : 45


      // sum range of integers from 1 to 10, inclusive
      System.out.printf("Sum of integers from 1 to 10: %d%n",
              IntStream.rangeClosed(1, 10).sum());
              // IntStream    : {3, 10, 6, 1, 4, 8, 2, 5, 9, 7}.  
              // .range(1, 10): {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}.
              // .sum()       : 55
   } 
} // end class IntStreamOperations
```

### Notes:
####Data Source
In the context of Java streams, a data source refers to the source from which data is consumed by a stream for processing. It can be a collection, an array, a generator function, or an I/O channel. In your example, int[] values serves as the data source when you create a stream using IntStream.of(values).

####Terminal Operations
Terminal operations are the final operations that trigger the processing of the data in the stream and after which the stream cannot be used anymore. They typically return a non-stream result or produce a side-effect (such as forEach). Examples include:

forEach(): Performs an action for each element of the stream.
count(): Returns the count of elements in the stream.
sum(): Sums the elements of a stream (specific to numeric streams like IntStream).
min(), max(): Returns the minimum or maximum element respectively.
reduce(): Performs a reduction on the elements of the stream using a given function.

####Intermediate Operations
Intermediate operations are operations that transform a stream into another stream. These operations are lazy; they do not process the data when they are called but instead create a new stream that, when traversed, contains the elements of the initial stream transformed by the intermediate operation. Examples include:

filter(): Returns a stream consisting of the elements that match the given predicate.
sorted(): Returns a stream with the elements sorted according to natural order or by a provided comparator.
map(): Transforms the elements of the stream by applying a function to each element.

####Lambda Expressions
Lambda expressions in Java are a concise way of representing an instance of a functional interface (an interface with a single abstract method). Lambda expressions implement the only abstract function and therefore decide the behavior of the function. They are used extensively in Java streams to provide implementations for functional interfaces like Predicate, Function, and Consumer. Examples from your code:

(value -> System.out.printf("%d ", value)): A Consumer lambda that prints each element.
((x, y) -> x + y): A BinaryOperator lambda used in reduce() to sum up elements.
(value -> value % 2 == 0): A Predicate lambda that filters even numbers.
These elements (data source, operations, lambda expressions) are fundamental to working with streams in Java and are used to perform complex data processing queries in a declarative way.
