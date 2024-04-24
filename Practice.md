# Java | Java Practice Codes

##  Recursion

### Factoriel Example;

Factoriel;

```
public class FactorielExample1 {
    public static void main(String [] args){

        int n = 21;
        factorial(n);
        System.out.println(factorial(n));
        
        for (int i=0; i <=n ; i++){
            System.out.print(factorial(i)+" ");
            System.out.println();
        }
    }
    
    private static long factorial(long n){
        if (n <= 1){
            return 1;
        }
        return n*factorial(n-1);
    }
}

```

Factoriel BigInteger;
```
import java.math.BigInteger;

public class FactorielExample2_BigInteger {
    public static void main(String [] args){
        
        BigInteger b = new BigInteger("1000");
        factorial(b);
        System.out.println(factorial(b));
        
        for (int i=0; i <=b.intValue() ; i++){
            String str = String.valueOf(i);
            BigInteger a = new BigInteger (str);
            System.out.print(factorial(a)+" ");
            System.out.println();
        }
    }
    
    private static BigInteger factorial(BigInteger n){
        if (n.compareTo(new BigInteger("1")) <= 0){
            return BigInteger.ONE;
        }
        
        return n.multiply(factorial(n.subtract(BigInteger.ONE)));
    }
}
```

### Fibonacci Example;

Base;
```

public class FibonacciExample{

    public static void main (String [] args){
        
        int n = 6;
        
        fibonacci(n);
        
        System.out.println(fibonacci(n)+" ");
    }

    private static long fibonacci(int n) {
        if (n<=1) {
            return n;
        }
        
        return (fibonacci(n-1) + fibonacci (n-2));
        
    }
}
```

FibonacciExample2_Memorization;
```
public class FibonacciExample2_Memorization{

    private static long fCache [];
    public static void main (String [] args){
        
        int n = 92;
        fCache = new long [n+1];
        fibonacci(n);
        System.out.println(fibonacci(n)+" ");
    }

    private static long fibonacci(int n) {
        if (n<=1) {
            return n;
        }
        
        if (fCache[n] != 0){
            return fCache[n] ;
        }
        
        fCache [n] = fibonacci(n-1) + fibonacci (n-2);
        return (fCache[n]);
    }
}
```

FibonacciExample3_BigInteger
```
import java.math.BigInteger;

public class FibonacciExample3_BigInteger {
    public static void main(String[] args) {
        for (int counter = 0; counter <= 40; counter++) {
            System.out.printf("Fibonacci of %d is: %d%n", counter, fibonacci(BigInteger.valueOf(counter)));
        }
    }

    private static BigInteger TWO = BigInteger.valueOf(2);

    public static BigInteger fibonacci(BigInteger n) {
        if (n.equals(BigInteger.ZERO) || n.equals(BigInteger.ONE)){ // base cases
            return n;
        }else{ // recursion step 
            return fibonacci(n.subtract(BigInteger.ONE)).add(fibonacci(n.subtract(TWO)));
        }
    }
}
```
