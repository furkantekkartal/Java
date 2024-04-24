# Java | Java Practice Codes

## 1. Recursion

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
