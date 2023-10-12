# road-to-dsa
### Decimal Formatter

**Problem:** Count the average of positive, negative, and zero numbers.

**Input:**
6 </br>
-4 3 -9 0 4 1</br>

**Output:**
0.500000</br>
0.333333</br>
0.166667

```java
import java.text.DecimalFormat;
import java.util.List;

public class DecimalFormatterExample {
    public static void plusMinus(List<Integer> arr) {
        int positives = 0, negatives = 0, zeros = 0;

        for (int num : arr) {
            if (num == 0) {
                zeros++;
            } else if (num < 0) {
                negatives++;
            } else {
                positives++;
            }
        }

        DecimalFormat df = new DecimalFormat("#.000000");
        System.out.println(df.format(positives / (double) arr.size()));
        System.out.println(df.format(negatives / (double) arr.size()));
        System.out.println(df.format(zeros / (double) arr.size()));
    }
}
```
### Mini Max Sum
**Problem:** Given five number find max and min number using four out of five numbers

**Input:**
1 2 3 4 5</br>

**Output:**
10 14

```java
 public static void miniMaxSum(List<Integer> arr) {
    // Write your code here
        int max=0;
        int totalSum = 0;
        for(int num: arr){
            totalSum = totalSum+ num;
        }
        int min = totalSum;
        
        for(int num: arr){
            int currSum = totalSum - num;
            if(currSum > max) max = currSum;
        }
        
         for(int num: arr){
            int currSum = totalSum - num;
            if(currSum < min) min = currSum;
        }
        
        System.out.print(min+" "+max);
        

    }
```
