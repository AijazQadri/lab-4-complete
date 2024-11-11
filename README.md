# lab-4-complete

**LAB TASK 1**
**1.	Write a program that takes two arrays of size 4 and swap the elements of those arrays.**

package com.mycompany.lab4labtask1;

import java.util.Arrays;

public class Lab4labtask1 {
    public static void main(String[] args) {
        int[] array1 = {10, 20, 30, 40};
        int[] array2 = {50, 60, 70, 80};

        System.out.println("Original arrays:");
        System.out.println("Array 1: " + Arrays.toString(array1));
        System.out.println("Array 2: " + Arrays.toString(array2));

        for (int i = 0; i < array1.length; i++) {
            int temp = array1[i];
            array1[i] = array2[i];
            array2[i] = temp;
        }

        System.out.println("\nSwapped arrays:");
        System.out.println("Array 1: " + Arrays.toString(array1));
        System.out.println("Array 2: " + Arrays.toString(array2));
    }
}


**LAB TASK 2**
**2.	Add a method in the class that takes array and merge it with the existing one.**

package com.mycompany.lab4labtask2;

public class Lab4labtask2 {
    static int[] array1 = {45, 56, 88};
    public static int[] merged(int[] array2) {
        int len = array1.length + array2.length;
        int[] merge = new int[len];
        for (int i = 0; i < array1.length; i++) {
            merge[i] = array1[i];
        }
        for (int i = 0; i < array2.length; i++) {
            merge[array1.length + i] = array2[i];
        }
        return merge;
    }
    public static void main(String[] args) {
        int[] array = {99, 89, 100, 566};
        int[] mer = merged(array);

        for (var i : mer) {
            System.out.print(i + " ");
        }
    }
}


**LAB TASK 3**

**3.	In a JAVA program, take an array of type string and then check whether the strings are palindrome or not.**
   
package com.mycompany.lab4labtask3;
public class Lab4labtask3 {
    public static boolean Palindrome(String str) {
        int left = 0;
        int right = str.length() - 1;
        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;  } 
    public static void main(String[] args) {
        String[] words = {"Aijaz", "Mobariz", "MOM", "DAD"};
        
        for (String word : words) {
            if (Palindrome(word)) {
                System.out.println(word + " is a palindrome.");
            } else {
                System.out.println(word + " is not a palindrome.");
            }
        }
    }
}


**LAB TASK 4**

**4.	Given an array of integers, count how many numbers are even and how many are odd.**
package com.mycompany.lab4labtask4;

public class Lab4labtask4 {

    public static void main(String[] args) {
       int[] numbers = {10, 11, 50, 48,49, 6};
        int evenCount = 0;
        int oddCount = 0;
        for (int number : numbers) {
            if (number % 2 == 0) {
                evenCount++;
            } else {
                oddCount++;
            }
        }
        System.out.println("Even numbers count: " + evenCount);
        System.out.println("Odd numbers count: " + oddCount);
    }
}


**LAB TASK 5**

**5.	Given two integer arrays, merge them and remove any duplicate values from the resulting array.**
   
package com.mycompany.lab4labtask5;
import java.util.*;
public class Lab4labtask5 {
static int[] array1={99,79,566,758};
    public static int[] merged(int[] array2){
        int len=array2.length + array1.length;
        int[] merge = new int[len];
        int j=0;
        int k=0;
        for(int i =0;i<len;i++){
            if (j>array1.length-1){
                merge[i]=array2[k];
                k++;
            }
            else{
                merge[i]=array1[j];
                j++;
            }
        }
        return merge;
    }
    public static int[] undoDuplicates(int[] array) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : array) {
            set.add(num);
        }
        int[] specialArray = new int[set.size()];
        int i = 0;
        for (int num : set) {
            specialArray[i++] = num;
        }
        return specialArray;
    }
    public static void main(String[] args) {
        int[] array={10,100,10,10};
        int[] mer = merged(array);
        System.out.print("Merged Array: " );
        for (int i: mer)
            System.out.print(i+" ");
        int[] Array = undoDuplicates(mer);
        System.out.println("\nMerged Array without Duplicates: " + Arrays.toString(Array));

    }
}


**Home TASK 1**

**1.	Write a program that takes an array of Real numbers having size 7 and calculate the sum and mean of all the elements. Also depict the memory management of this task.**

package com.mycompany.lab4hometask1;
public class Lab4hometask1 {
    public static void main(String[] args) {
        double[] numbers = new double[7];
        numbers[0] = 5.2;
        numbers[1] = 8.4;
        numbers[2] = 3.1;
        numbers[3] = 7.6;
        numbers[4] = 2.3;
        numbers[5] = 9.5;
        numbers[6] = 4.8;       
        double sum = 0;
        for (int i = 0; i < numbers.length; i++) {
            sum += numbers[i];
        }       
        double mean = sum / numbers.length;
        System.out.println("Sum of elements: " + sum);
        System.out.println("Mean of elements: " + mean);
    }
}


**Home TASK 2**

**2.	Add a method in the same class that splits the existing array into two. The method should search a key in array and if found splits the array from that index of the key.**
   
package com.mycompany.lab4hometask2;
import java.util.*;
public class Lab4hometask2 {
 public static int[][] split(int[] arr) {
        System.out.println("Enter the clue to split the array:");
        Scanner Sc = new Scanner(System.in);
        int clue = Sc.nextInt();
        int clueIndex = -1;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == clue) {
                clueIndex = i+1;
                break;
            }
        }
        if (clueIndex == -1) {
            System.out.print("clue not found in the array.");
            return new int[][]{{}, {}};
        }
        int[] Part1 = new int[clueIndex];
        int[] Part2 = new int[arr.length - clueIndex];
        for (int i = 0; i < clueIndex; i++) {
            Part1[i] = arr[i];
        }
        for (int i = clueIndex; i < arr.length; i++) {
            Part2[i - clueIndex] = arr[i];
        }
        return new int[][]{Part1, Part2};
    }
    public static void main(String[] args) {
        int[] arr1 = {10,20,30,40,50,60,70};
        int[][] splitArray = split(arr1);
        if (splitArray[0].length > 0 || splitArray[1].length > 0) {
            System.out.println("First part of the array:");
            for (int num : splitArray[0])
                System.out.print(num + " ");
            System.out.println("\nSecond part of the array:");
            for (int num : splitArray[1]) 
                System.out.print(num + " ");
        }
    }
}


**Home TASK 3**

**3.	Given an array of distinct integers and a target integer, return all unique combinations of numbers that add up to the target. Each number can be used only once in the combination.**

**Home TASK 4**

**4.	You are given an array containing n distinct numbers taken from 0, 1, 2, ..., n. Write a program to find the one number that is missing from the array.**
   
package com.mycompany.lab4hometask4;

public class Lab4hometask4 {

    public static int MissingNumber(int[] arr, int n) {
        int sum_Array = 0;
        int sum_Numbers = n * (n + 1) / 2;

        for (int num : arr) {
            sum_Array += num;
        }
        return sum_Numbers - sum_Array;
    }

    public static void main(String[] args) {
        int[] arr = {4, 1, 3, 4};
        int n = 10;
        int missingNumber = MissingNumber(arr, n);
        System.out.println("The missing number is: " + missingNumber);
    }
}


**Home TASK 5**

**5.	You are given an array of integers. Write a program to sort the array such that it follows a zigzag pattern: the first element is less than the second, the second is greater than the third, and so on.**
   
package com.mycompany.lab4hometask5;
import java.util.*;
public class Lab4hometask5 {
    public static void zigzag(int[] arr) {
        Arrays.sort(arr);
        for (int i = 1; i < arr.length; i += 2) {
            if (i + 1 < arr.length && arr[i] < arr[i + 1]) {
                int temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
    }
    public static void main(String[] args) {
        int[] arr = {40, 3, 70, 8, 60, 2, 10}; 
        System.out.println("Original array: " + Arrays.toString(arr)); 
        zigzag(arr);
        System.out.println("Zigzag sorted array: " + Arrays.toString(arr));
    }
}
