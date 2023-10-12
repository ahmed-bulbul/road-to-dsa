# road-to-dsa

## [LinkedList](#linkedlist)
 - [Create Linked List](#create-linked-list)

## [Week 1](#week-1)

- [Decimal Formatter](#decimal-formatter)
- [Mini Max Sum](#mini-max-sum)
- [Time Conversion](#time-conversion)

## [Week 2](#week-2)

- [Problem 1](#problem-1)
- [Problem 2](#problem-2)
- [Problem 3](#problem-3)





## LinkedList
### Create Linked List

**লিঙ্ক লিস্ট কিভাবে তৈরি করতে হয় ** 
প্রথমে আমাদের এক্টি Node ক্লাস তৈরি করতে হবে 
```java
 public static class Node{
        int data;
        Node next;
        Node(int data){
            this.data = data;
        }
    }
```
এখানে দুইটি ভেরিয়েবল একটি ডাটা এবং অন্যটি নেক্সট । এখন দেখব লিঙ্ক লিস্ট এ কিভাবে ভ্যলু অ্যাড এবং রিলেশন তৈরি করতে হয় । 
```java
public static void main(String[] args) {
        Node a = new Node(100);
        Node b = new Node(13);
        Node c = new Node(4);
        Node d = new Node(5);
        Node e = new Node(12);
        Node f = new Node(10);

        a.next=b;
        b.next=c;
        c.next=d;
        d.next=e;
        e.next=f;
}
```


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
