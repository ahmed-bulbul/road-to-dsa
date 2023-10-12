# road-to-dsa

<h3> Decimal Formatter Java </h3>
```java
import java.text.DecimalFormat;

public class DecimalFormatterExample {
    public static void main(String[] args) {
        DecimalFormat df = new DecimalFormat("#.000000");
        int x = 5;
        int size = 10;
        System.out.println(df.format(x / (double) size));
    }
}
