# DSA Foundation

## [LinkedList](#linkedlist)
 - [Create Linked List](#create-linked-list)
 - [Find nth Node From the End](#find-nth-node-from-the-end)
 - [Remove nth Node From the End](#remove-nth-node-from-the-end)


   
# Hacker Rank 3 Month interview preparation 
## [Week 1](#week-1)

- [Decimal Formatter](#decimal-formatter)
- [Mini Max Sum](#mini-max-sum)
- [Time Conversion](#time-conversion)
- [Breaking The Records](#breaking-the-records)
- [Divisible Sum pairs](#divisible-sum-pairs)
- [Camel Case 4](#camel-case-4)
- [Mock Test 1](#mock-test-1)
- [এই ৭ দিনে কি শিখলাম](#এই-৭-দিনে-কি-শিখলাম)
  
  

## [Week 2](#week-2)

- [Lonely Integer](#lonely-integer)
- [Problem 2](#problem-2)
- [Problem 3](#problem-3)

- ## [Week 3](#week-3)

- [Problem 1](#problem-1)
- [Problem 2](#problem-2)
- [Problem 3](#problem-3)




# Leetcode Problems & Solutions : [Top Interview Question](https://leetcode.com/explore/interview/card/top-interview-questions-easy/)
## [Array](#leetcode-array)
 - [Remove Duplicates From Sorted Array](#remove-duplicates-from-sorted-array)
 - 





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
এখন দেখব অ্যাডকৃত ডাটা কিভাবে প্রদর্শন করতে হয় 

```java
public static void display(Node head){
        Node temp = head;
        while (temp!=null){
            System.out.print(temp.data+" ");
            temp=temp.next;
        }
        System.out.println();
    }
```
### Find nth Node From the End
Solution 1: 
```java
public static Node nthNode(Node head,int n){
        int size = 0;
        Node temp = head;

        while (temp!=null){
            size++;
            temp = temp.next;
        }
        int m = size - n +1; //mth node from start
        temp = head;
        for(int i=1;i<=m-1;i++){
            temp = temp.next;
        }
        return temp;

    }
```
Solution 2: 
```java
public static Node nthNode2(Node head,int n){
        Node slow = head;
        Node fast = head;

        for(int i=0;i<n;i++){
            fast = fast.next;
        }

        while(fast!=null){
            slow = slow.next;
            fast=fast.next;
        }
        return slow;
    }
```
### Remove nth Node From the End
```java
public static void deleteNthFromEnd(Node head, int n){
        Node slow = head;
        Node fast = head;

        for(int i=0;i<n;i++){
            fast = fast.next;
        }

        while (fast.next!=null){
            slow = slow.next;
            fast = fast.next;
        }
        slow.next = slow.next.next;

    }
```

## Leetcode Array
### Remove Duplicates From Sorted Array
```
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
Solution:
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        
       if (nums.length == 0) {
            return 0;
        }

        int k = 1;

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;
        
    }
}
```
সমাধান টি একটু বুঝার চেষ্টা করি, ধরি লিস্ট ই [ ১,২,৩্‌,৩,৪]  । একটা ফ্ল্যাগ ভেরিয়েবল k = 1. লুপের ভিতর যদি খেয়াল করি, ২ এবং ১ যদি সমান না হয় তাহলে ২ এর পজিশনে ২ই বসবে এবং কে এর মান ইঙ্ক্রিমেন্ট হবে । 
এখন কে এর মান ২ । এখন ২ এবং ৩ এর মধ্যে তুলনা হবে । ২ এওং ৩ সেইম না , সুতরাং ৩ তার নিজস্ব জায়গায় ই বসবে এবং কে এর মান ১ বাড়বে । এখন কে এর মান ৩ । ৩ এবং ৩ এর মধ্যে তুলনা হবে । যেহেতু ৩ ==৩ সুতরাং কে এর মান বাড়বে না । 
এখন ৩ এবং ৪ এর মধ্যে তুলনা হবে । ৩ এবং যেহেতু ভিন্ন , সেহেতু এরের কে তম পজিশন কে = ৩ , মানে ৩ এর জায়গায় ৪ বসবে । তাহলে ফাইনাল এরে হল [ ১, ২ ,৩ ৪ - ]


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

### Breaking The Records
**Problem** Given an array of scores of a player, need to find how many times he breaks his highest and lowest score.

**Input:**
10 5 20 20 4 5 2 25 1</br>

**Output:**
2 4

```java
public static List<Integer> breakingRecords(List<Integer> scores) {
        int min = scores.get(0);
        int max = scores.get(0);
        int minCount = 0;
        int maxCount = 0;

        for(int i=1;i<scores.size();i++){
            if(scores.get(i) < min){
                min = scores.get(i);
                minCount++;
            }
            if(scores.get(i) > max){
                max = scores.get(i);
                maxCount++;
            }
        }
        return Arrays.asList(maxCount,minCount);
    }
```

### Divisible Sum pairs 
**Problem** Given an array of integers and a positive integer k, determine the number of (i,j) pairs where i < j and ar[i] + ar[j] is divisible by k.


**Input:**
6 3</br>
1 3 2 6 1 2</br>

**Output:**
5

```java
 public static int divisibleSumPairs(int n, int k, List<Integer> ar) {
    // Write your code here
    
        int count=0;
        for(int i=0;i<ar.size();i++){
            for(int j=i+1;j<ar.size();j++){
                
                int tempSum = ar.get(i) + ar.get(j);
                
                if(tempSum%k==0 ){
                    count++;
                }
            }
        }
        
        return count;

    }
```

### Camel Case 4
**Problem** Camel case 4 problem

**Input**
S;M;plasticCup() </br>
C;V;mobile phone  </br>
C;C;coffee machine  </br>
S;C;LargeSoftwareBook  </br>
C;M;white sheet of paper  </br>
S;V;pictureFrame </br> 

**Output**
plastic cup  </br>
mobilePhone  </br>
CoffeeMachine  </br>
large software book  </br>
whiteSheetOfPaper()  </br>
picture frame

```java

import java.util.Scanner;

public class CamelCase {


    public static void main(String[] args) {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */

        Scanner scanner = new Scanner(System.in);

        while (scanner.hasNextLine()) {
            String line = scanner.nextLine();
            String[] parts = line.split(";");
            if (parts.length != 3) {
                continue; // Skip invalid input lines
            }

            String operation = parts[0];
            String type = parts[1];
            String input = parts[2];

            if (operation.equals("S")) {
                if (type.equals("M")) {
                    String[] words = splitCamelCaseMethod(input);
                    System.out.println(String.join(" ", words));
                } else if (type.equals("C")) {
                    String converted = splitCamelCaseClass(input);
                    System.out.println(converted);
                } else if (type.equals("V")) {
                    String[] words = splitCamelCaseVariable(input);
                    System.out.println(String.join(" ", words));
                }
            } else if (operation.equals("C")) {
                if (type.equals("V")) {
                    String converted = combineCamelCaseVariable(input);
                    System.out.println(converted);
                } else if (type.equals("C")) {
                    String converted = combineCamelCaseClass(input);
                    System.out.println(converted);
                } else if (type.equals("M")) {
                    String converted = combineCamelCaseMethod(input);
                    System.out.println(converted);
                }
            }

        }
    }

    public static String[] splitCamelCaseMethod(String input) {
        String methodName = input.substring(0, input.indexOf("("));
        String[] words = splitCamelCaseVariable(methodName);
        return words;
    }

    public static String splitCamelCaseClass(String input) {
        String[] words = input.split("(?<=.)(?=\\p{Lu})");
        for (int i = 0; i < words.length; i++) {
            words[i] = words[i].substring(0, 1).toLowerCase() + words[i].substring(1);
        }
        return String.join(" ", words);
    }

    public static String[] splitCamelCaseVariable(String input) {
        String[] words = input.split("(?<=.)(?=\\p{Lu})");
        for (int i = 0; i < words.length; i++) {
            words[i] = words[i].substring(0, 1).toLowerCase() + words[i].substring(1);
        }
        return words;
    }

    public static String combineCamelCaseVariable(String input) {
        String[] words = input.split(" ");
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < words.length; i++) {
            if (i == 0) {
                result.append(words[i]);
            } else {
                result.append(words[i].substring(0, 1).toUpperCase()).append(words[i].substring(1));
            }
        }
        return result.toString();
    }

    public static String combineCamelCaseClass(String input) {
        String[] words = input.split(" ");
        StringBuilder result = new StringBuilder();
        for (String word : words) {
            result.append(word.substring(0, 1).toUpperCase()).append(word.substring(1));
        }
        return result.toString();
    }

    public static String combineCamelCaseMethod(String input) {
        String[] words = input.split(" ");
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < words.length; i++) {
            if (i == 0) {
                result.append(words[i]);
            } else {
                result.append(words[i].substring(0, 1).toUpperCase()).append(words[i].substring(1));
            }
        }
        return result.toString() + "()";
    }
}
```

### Mock Test 1
**Problems** Find the median. 

**Input**

7 </br>
0 1 2 4 6 5 3

**Output**

3
```java

    public static int findMedian(List<Integer> arr) {
    // Write your code here
    arr.sort(null);
    int middle = arr.size()/2;
    return arr.get(middle);

    }
```
### এই ৭ দিনে কি শিখলাম
**ডেসিমাল ফর্মেটার ঃ** 

ডেসিমাল ফরমেট এর জন্য আমরা DecimalFormat ক্লাস ব্যবহার করি এবং এর মদ্ধে আমরা ফরমেট পাস করে দিতে পারি । 
```java
DecimalFormat df = new DecimalFormat("#.000000");
```
টাইম কিভাবে কনভার্শন করতে হয় তা শিখেছি । 

## Week 2

### Lonely Integer
**Problem** Given an array of integers, where all elements but one occur twice, find the unique element.

Example
a=[1,2,3,4,3,2,1]
The unique element is 4

```java
public static int lonelyinteger(List<Integer> a) {
    // Write your code here
    
        Map<Integer,Integer> map = new HashMap<>();
        
        for(int i : a){
            if(!map.containsKey(i)){
                map.put(i, 1);
            }else{
                map.put(i, map.get(i)+1);
            }
        }
        
      
        for (Map.Entry<Integer, Integer> entry : map.entrySet()){
            if(entry.getValue()==1){
                return entry.getKey();
            }
        }
        
        return 0;
        
        

    }
```

