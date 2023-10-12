# road-to-dsa
## Week 1
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

        long max=Integer.MIN_VALUE;
        long min = Integer.MAX_VALUE;
        long sum=0;
        
        
        for(int num: arr){
            sum = sum+num;
            if(num < min){
                min = num;
            }
            if(num > max){
                max = num;
            }
            
        }
        System.out.println(String.format("%d %d", sum-max, sum-min));
    }
```
### Time Conversion
**Problem:** Given time in AM/AM means 12 hour format need to conver it to 24 - hour format
**Input:**
07:05:45PM </br>

**Output:**
19:05:45

```java
  public static String timeConversion(String s) {
       int hour = Integer.valueOf(s.substring(0,2));

        if(s.endsWith("AM")){
            hour = (hour==12)?0:hour;
        }else{
            hour = (hour==12)?hour:hour+12;
        }

        return String.format("%02d%s",hour,s.substring(2,s.length()-2));
    }
```
