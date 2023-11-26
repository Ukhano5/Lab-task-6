# Lab-task-6
12370 
ABBOTTABAD UNIVERSITY OF SCIENCE AND TECHNOLOGY 
Department of Computer Science 
 Lab task # 6–  fall -2023 
Class: BSSE-3 C
Date: 12/08/2023 
Subject: DSA 
Instructor: Fahad Ali Khan
Submitted By: Muhammad Umair
                 Roll no:12370
Roll No : 12370 
Q1: Create a function in python that take two string as input and determine if they are anagram. Utilize a hash table to efficiently compare the character frequencies in two strings

Answer :
def are_anagrams(str1, str2):
    # Removing spaces and converting to lowercase for case-insensitivity
    str1 = str1.replace(" ", "").lower()
    str2 = str2.replace(" ", "").lower()

    # Check if lengths are equal
    if len(str1) != len(str2):
        return False

    # Create hash tables to store character frequencies
    freq_table1 = {}
    freq_table2 = {}

    # Populate hash table for str1
    for char in str1:
        freq_table1[char] = freq_table1.get(char, 0) + 1

    # Populate hash table for str2
    for char in str2:
        freq_table2[char] = freq_table2.get(char, 0) + 1

    # Compare the two hash tables
    return freq_table1 == freq_table2


str1 = "listen"
str2 = "silent"
result = are_anagrams(str1, str2)
print(result)  # Output: True
Out put 
True 

QUESTION NO 2 :
Write a python program that take a list of integers as input and return dictionary where keys are unique number from the list and values are the frequency of those numbers

ANSWER 

def count_frequency(input_list):
    frequency_dict = {}
    
    for num in input_list:
        frequency_dict[num] = frequency_dict.get(num, 0) + 1

    return frequency_dict

# Example 
input_numbers = [1, 2, 3, 1, 2, 4, 5, 6, 5, 4, 7, 8, 9, 9, 8]
result_dict = count_frequency(input_numbers)
print(result_dict)

OUT PUT 
{1: 2, 2: 2, 3: 1, 4: 2, 5: 2, 6: 1, 7: 1, 8: 2, 9: 2}

Question No 3 

Implement a python function that gives an array of integers find the length of the longest sub array with a sum equal to specified value k. Use a hash table to track cumulative sums efficiently

Answer :
def longest_subarray_sum_k(arr, k):
    cumulative_sum = 0
    max_length = 0
    sum_indices = {0: -1}  # Using a hash table to store cumulative sums and their indices

    for i, num in enumerate(arr):
        cumulative_sum += num

        # Check if (cumulative_sum - k) is in the hash table
        if cumulative_sum - k in sum_indices:
            max_length = max(max_length, i - sum_indices[cumulative_sum - k])

        # Store the index of the cumulative sum in the hash table
        if cumulative_sum not in sum_indices:
            sum_indices[cumulative_sum] = i

    return max_length

# Example usage:
arr = [10, 5, 2, 7, 1, 9]
k = 15
result = longest_subarray_sum_k(arr, k)
print(result)
OUT PUT 
4
