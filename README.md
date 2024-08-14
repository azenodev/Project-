using System;

namespace MyLibrary
{
    public class NumberPrograms
    {
        // 1. Factorial
        public int Factorial(int number)
        {
            if (number == 0 || number == 1)
                return 1;
            return number * Factorial(number - 1);
        }

        // 2. Fibonacci
        public int Fibonacci(int n)
        {
            if (n <= 1)
                return n;
            return Fibonacci(n - 1) + Fibonacci(n - 2);
        }

        // 3. Palindrome (Number)
        public bool IsPalindrome(int number)
        {
            int temp = number, reverse = 0;
            while (temp > 0)
            {
                reverse = reverse * 10 + temp % 10;
                temp /= 10;
            }
            return number == reverse;
        }

        // 4. Magic Number
        public bool IsMagicNumber(int number)
        {
            while (number > 9)
            {
                int sum = 0;
                while (number > 0)
                {
                    sum += number % 10;
                    number /= 10;
                }
                number = sum;
            }
            return number == 1;
        }

        // 5. Reverse Number
        public int ReverseNumber(int number)
        {
            int reverse = 0;
            while (number > 0)
            {
                reverse = reverse * 10 + number % 10;
                number /= 10;
            }
            return reverse;
        }

        // 6. Armstrong Number
        public bool IsArmstrongNumber(int number)
        {
            int temp = number, sum = 0;
            while (temp > 0)
            {
                int digit = temp % 10;
                sum += digit * digit * digit;
                temp /= 10;
            }
            return sum == number;
        }

        // 7. Perfect Number
        public bool IsPerfectNumber(int number)
        {
            int sum = 0;
            for (int i = 1; i < number; i++)
            {
                if (number % i == 0)
                    sum += i;
            }
            return sum == number;
        }

        // 8. Prime Number
        public bool IsPrime(int number)
        {
            if (number <= 1)
                return false;
            for (int i = 2; i <= Math.Sqrt(number); i++)
            {
                if (number % i == 0)
                    return false;
            }
            return true;
        }

        // 9. Sum of Digits
        public int SumOfDigits(int number)
        {
            int sum = 0;
            while (number > 0)
            {
                sum += number % 10;
                number /= 10;
            }
            return sum;
        }

        // 10. GCD (Greatest Common Divisor)
        public int GCD(int a, int b)
        {
            while (b != 0)
            {
                int temp = b;
                b = a % b;
                a = temp;
            }
            return a;
        }

        // 11. LCM (Least Common Multiple)
        public int LCM(int a, int b)
        {
            return (a * b) / GCD(a, b);
        }

        // 12. Count Digits
        public int CountDigits(int number)
        {
            int count = 0;
            while (number > 0)
            {
                count++;
                number /= 10;
            }
            return count;
        }

        // 13. Power of a Number
        public int Power(int baseNum, int exp)
        {
            int result = 1;
            for (int i = 0; i < exp; i++)
            {
                result *= baseNum;
            }
            return result;
        }

        // 14. Sum of First N Natural Numbers
        public int SumOfFirstNNumbers(int n)
        {
            return n * (n + 1) / 2;
        }

        // 15. Factorial using Iteration
        public int FactorialIterative(int number)
        {
            int result = 1;
            for (int i = 1; i <= number; i++)
            {
                result *= i;
            }
            return result;
        }
    }
}





using System;

namespace MyLibrary
{
    public class StringPrograms
    {
        // 1. Palindrome (String)
        public bool IsPalindrome(string str)
        {
            int len = str.Length;
            for (int i = 0; i < len / 2; i++)
            {
                if (str[i] != str[len - i - 1])
                    return false;
            }
            return true;
        }

        // 2. Reverse String
        public string ReverseString(string str)
        {
            char[] charArray = str.ToCharArray();
            Array.Reverse(charArray);
            return new string(charArray);
        }

        // 3. Count Vowels
        public int CountVowels(string str)
        {
            int count = 0;
            string vowels = "aeiouAEIOU";
            foreach (char c in str)
            {
                if (vowels.Contains(c))
                    count++;
            }
            return count;
        }

        // 4. To Upper Case
        public string ToUpperCase(string str)
        {
            return str.ToUpper();
        }

        // 5. To Lower Case
        public string ToLowerCase(string str)
        {
            return str.ToLower();
        }

        // 6. Count Words in a String
        public int CountWords(string str)
        {
            return str.Split(' ').Length;
        }

        // 7. Find Longest Word
        public string FindLongestWord(string str)
        {
            string[] words = str.Split(' ');
            string longestWord = "";
            foreach (string word in words)
            {
                if (word.Length > longestWord.Length)
                    longestWord = word;
            }
            return longestWord;
        }

        // 8. Reverse Words in a String
        public string ReverseWords(string str)
        {
            string[] words = str.Split(' ');
            Array.Reverse(words);
            return string.Join(" ", words);
        }

        // 9. Check Anagram
        public bool IsAnagram(string str1, string str2)
        {
            char[] char1 = str1.ToLower().ToCharArray();
            char[] char2 = str2.ToLower().ToCharArray();
            Array.Sort(char1);
            Array.Sort(char2);
            return new string(char1) == new string(char2);
        }

        // 10. Remove Duplicates from String
        public string RemoveDuplicates(string str)
        {
            string result = "";
            foreach (char c in str)
            {
                if (!result.Contains(c))
                    result += c;
            }
            return result;
        }
    }
}





using System;
using MyLibrary;

namespace MyApplication
{
    class Program
    {
        static void Main(string[] args)
        {
            var numberProgram = new NumberPrograms();
            var stringProgram = new StringPrograms();

            // Number Programs
            Console.WriteLine("Factorial of 5: " + numberProgram.Factorial(5));
            Console.WriteLine("5th Fibonacci number: " + numberProgram.Fibonacci(5));
            Console.WriteLine("Is 121 Palindrome: " + numberProgram.IsPalindrome(121));
            Console.WriteLine("Is 1234 a Magic Number: " + numberProgram.IsMagicNumber(1234));
            Console.WriteLine("Reverse of 12345: " + numberProgram.ReverseNumber(12345));
            Console.WriteLine("Is 153 an Armstrong Number: " + numberProgram.IsArmstrongNumber(153));
            Console.WriteLine("Is 28 a Perfect Number: " + numberProgram.IsPerfectNumber(28));
            Console.WriteLine("Is 17 a Prime Number: " + numberProgram.IsPrime(17));
            Console.WriteLine("Sum of digits of 12345: " + numberProgram.SumOfDigits(12345));
            Console.WriteLine("GCD of 15 and 20: " + numberProgram.GCD(15, 20));
            Console.WriteLine("LCM of 15 and 20: " + numberProgram.LCM(15, 20));
            Console.WriteLine("Count of digits in 12345: " + numberProgram.CountDigits(12345));

            Console.WriteLine("3 raised to the power of 4: " + numberProgram.Power(3, 4));
            Console.WriteLine("Sum of first 10 natural numbers: " + numberProgram.SumOfFirstNNumbers(10));
            Console.WriteLine("Factorial of 5 using iteration: " + numberProgram.FactorialIterative(5));

            // String Programs
            Console.WriteLine("Is 'radar' a Palindrome: " + stringProgram.IsPalindrome("radar"));
            Console.WriteLine("Reverse of 'hello': " + stringProgram.ReverseString("hello"));
            Console.WriteLine("Number of vowels in 'hello': " + stringProgram.CountVowels("hello"));
            Console.WriteLine("'hello' in Upper Case: " + stringProgram.ToUpperCase("hello"));
            Console.WriteLine("'HELLO' in Lower Case: " + stringProgram.ToLowerCase("HELLO"));
            Console.WriteLine("Number of words in 'Hello world': " + stringProgram.CountWords("Hello world"));
            Console.WriteLine("Longest word in 'The quick brown fox': " + stringProgram.FindLongestWord("The quick brown fox"));
            Console.WriteLine("Reversed words in 'Hello world': " + stringProgram.ReverseWords("Hello world"));
            Console.WriteLine("Are 'listen' and 'silent' Anagrams: " + stringProgram.IsAnagram("listen", "silent"));
            Console.WriteLine("String after removing duplicates from 'programming': " + stringProgram.RemoveDuplicates("programming"));
        }
    }
}
