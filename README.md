# road-to-dsa
### Decimal Formatter

**Problem:** Count the average of positive, negative, and zero numbers.

**Input:**
6
-4 3 -9 0 4 1

**Output:**
0.500000
0.333333
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
