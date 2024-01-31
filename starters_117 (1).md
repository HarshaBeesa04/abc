# Codechef_starters_117_Div3

<!-- First Question -->
# Weapon Choice
<details>
<summary>Python</summary>

```python
import math
t = int(input())
for _ in range(t):
    h,x,y1,y2,k = map(int,input().split())
    c1 = math.ceil(h/x)
    if y1<=x:
        print(c1)
        continue
    if y1*k>=h:
        print(math.ceil(h/y1))
    else:
        count = k
        h-=(y1*k)
        count+=(math.ceil(h/y2))
        print(min(count,c1))
```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>
#include <cmath>

using namespace std;

/**
 * @brief Calculates the minimum hits needed to defeat a boss with given weapons and health.
 * 
 * @param h The boss's health.
 * @param x The gun's damage per hit.
 * @param y1 The laser's initial damage per hit.
 * @param y2 The laser's lowered damage per hit.
 * @param k The threshold of laser hits before output drops.
 * @return The minimum number of hits needed to defeat the boss.
 */
int calculateMinHits() {

    int h, x, y1, y2, k;
    
    cin >> h >> x >> y1 >> y2 >> k;
    
    int gunHits = ceil((double)h / x); // Minimum hits needed with the gun

    // If laser's initial damage is less than or equal to gun damage, use gun
    if (y1 <= x) {
        return gunHits;
    }

    // If laser can defeat the boss within its threshold, use laser
    if (y1 * k >= h) {
        return ceil((double)h / y1); 
    }

    // Calculate hits needed after laser's output drops
    int laserHits = k + ceil((double)(h - (y1 * k)) / y2);

    // Return the minimum of gun hits and laser hits
    return min(gunHits, laserHits);
}

int main() {
    int t;
    cin >> t;

    while (t--) {

        cout << calculateMinHits(h, x, y1, y2, k) << endl;
    }

    return 0;
}
```
</details>


<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class ChefAndBoss {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int h = scanner.nextInt();
            int x = scanner.nextInt();
            int y1 = scanner.nextInt();
            int y2 = scanner.nextInt();
            int k = scanner.nextInt();

            int gunHits = (int) Math.ceil((double) h / x);

            if (y1 <= x) {
                System.out.println(gunHits);
                continue;
            }

            if (y1 * k >= h) {
                System.out.println((int) Math.ceil((double) h / y1));
            } else {
                int laserHits = k + (int) Math.ceil((double) (h - (y1 * k)) / y2);
                System.out.println(Math.min(gunHits, laserHits));
            }
        }
    }
}
```
</details>

<!-- Second Question -->
# Spell Shortening

<details>
<summary>Python</summary>

```python
import sys

def lexicographic_string():
    t = int(sys.stdin.readline())

    for _ in range(t):
        n = int(sys.stdin.readline())
        v = sys.stdin.readline().strip()

        max_index = -1
        for i in range(1, n):
            if v[i - 1] > v[i]:
                max_index = i - 1
                break

        if max_index == -1:
            max_index = n - 1

        v = v[:max_index] + v[max_index + 1:]
        print(v)

if __name__ == "__main__":
    lexicographic_string()

```

</details>

<details>
<summary>Cpp</summary>
  
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	/**
	 * t - testcases
     * n - size of the string
     * v - input string
	 */
    int t;
    cin >> t;
    
    while (t--) {
        int n;
        cin >> n;
        
        string v;
        cin >> v;
        
        /**
         * The Logic :
         * ---------
         * - The lexicographically least string after removing a character, is what we are after
         * - consider the examples in the testcases
         *      ab, if the string is already lexographically sorted
         *      What we can do is remove the largest character so we
         *      can have the lexicographically short string
         *      
         *      ex : abeg --> abe;
         *           defgh --> defh;
         *      
         *      Any other character removal results in rather larger string
         * 
         * - if we happen to find characters that are not in lexographically sorted order, what
         *   we can do is find the first out of order character and remove it, so that the operation
         *   results in a lexigraphically small string 
         *      ex : magic --> agic, 1st out of order `m > a`
         *           author --> athor 1st out of order `u > t` 
         */

        // the max element out of found `out of order` pair
        int max_index = -1;
        
        for (int i = 1; i < n; i++) {
            if (v[i - 1] > v[i]) {
                max_index = i - 1;
                break;
            }
        }
        
        if (max_index == -1)
            max_index = n - 1;
        
        v.erase(v.begin() + max_index);
        
        cout << v << endl;
        
    }
    return 0;
}
```

</details>
<!-- Java -->
<details>
<summary>Java</summary>

```Java
import java.util.Scanner;

public class LexicographicString {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            String v = scanner.next();

            int maxIndex = -1;
            for (int i = 1; i < n; i++) {
                if (v.charAt(i - 1) > v.charAt(i)) {
                    maxIndex = i - 1;
                    break;
                }
            }

            if (maxIndex == -1) {
                maxIndex = n - 1;
            }

            StringBuilder sb = new StringBuilder(v);
            sb.deleteCharAt(maxIndex);
            v = sb.toString();

            System.out.println(v);
        }
    }
}

```
</details>

<!-- Third Quesion -->
# Not Prime Permutation

<details>
<summary>Python</summary>

```python
import sys

def non_prime_permutation():
    t = int(sys.stdin.readline())

    for _ in range(t):
        n = int(sys.stdin.readline())
        v = list(map(int, sys.stdin.readline().split()))

        if n <= 2:
            print(-1)
            continue

        for i in v:
            print(3 if i == 1 else 1 if i == 3 else i, end=" ")
        print()

if __name__ == "__main__":
    non_prime_permutation()

```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
    int t;
    cin >> t;
    
    while (t--) {
        
        int n;
        cin >> n;
        
        vector<int> v(n);
        
        for (auto & i : v) {
            cin >> i;
        }

        /**
         * @brief 
         * 
         * The Logic :
         * *********
         * 
         * The permutation possible here to make the given permutation's
         * combo sum a non-prime is --> Adding itself to every element. Now
         * the sum has a factor 2 making it a non prime
         * 
         * However this has a down side
         * 
         * in the case of element 1, if we add it to itself we get 2, which
         * is prime
         *      so every time we get 1 we print 3 making it's sum 4
         *      and at 3 we print 1, making the sum again as 4
         * 
         * if the size of permutation is less than or equal to 2 we don't
         * have the luxury of doing the swap any more. so print -1 
         * 
         */
        
        if (n <= 2) {
            cout << "-1" << endl;
            continue;
        }
        
        vector<int> t = v;
        
        for (auto i : v) {
            if (i == 1)
                cout << 3 << " ";
            else if (i == 3)
                cout << 1 << " ";
            else 
                cout << i << " ";
        }
        cout << endl;
    }
    return 0;
}

```
</details>

<details>
<summary>Java</summary>

```Java
import java.util.ArrayList;
import java.util.Scanner;

public class NonPrimePermutation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        while (t-- > 0) {
            int n = scanner.nextInt();
            ArrayList<Integer> v = new ArrayList<>();

            for (int i = 0; i < n; i++) {
                v.add(scanner.nextInt());
            }

            if (n <= 2) {
                System.out.println("-1");
                continue;
            }

            for (int i : v) {
                System.out.print((i == 1) ? 3 : (i == 3) ? 1 : i + " ");
            }
            System.out.println();
        }
    }
}
```
</details>

<!-- Fourth Question -->
# Equality Etiquette

<details>
    <summary>Python</summary>

```python
import math
t = int(input())
for _ in range(t):
    a,b = map(int,input().split())
    diff = abs(a-b)
    #base cases
    if diff == 0:
        print("0")
        continue
    if diff == 1:
        print("1")
        continue
    #approximation of the quadratic equation formula
    #Binary search can also be used but this is much simpler
    #diff = n(n+1)/2
   #  n^2+n-2*diff = 0
   #  by using the quadratic equation we can approxmiate that n is less that sqrt of 2d
    n = math.isqrt(2*diff)
    #the sum should be atleast diff so that we can make two sets which can be equal
    while n*(n+1)//2<diff:
        n+=1
# if difference we want is odd but your sum is even it is not possible to get
    while (n*(n+1)//2)%2 != diff%2:
        n+=1
    print(n)
#In binary search approach you will find a number such that difference is 
#less than or equal to sum of numbers till that number and you will adjust
#the odd even parity just how we adjusted here
```
</details>


<details>
  	<summary>C++</summary>
  
```cpp
#include <iostream>
#include <cmath>

using namespace std;

/**
 * @brief Calculates the minimum number of operations required to make two sets equal.
 *
 * @param a The first element in the first set.
 * @param b The first element in the second set.
 * @return int The minimum number of operations required.
 */
int calculateOperations(int a, int b) {
    int diff = abs(a - b);

    // Base cases
    if (diff == 0) {
        return 0;
    }
    if (diff == 1) {
        return 1;
    }

    // Approximate the value of n using the quadratic formula
    int n = (int)sqrt(2 * diff);  // Note: cmath::isqrt not available in C++

    // Ensure the sum is at least equal to the difference
    while (n * (n + 1) / 2 < diff) {
        n++;
    }

    // Adjust for odd/even parity if necessary
    while ((n * (n + 1) / 2) % 2 != diff % 2) {
        n++;
    }

    return n;
}

int main() {
    int t;
    cin >> t;

    for (int i = 0; i < t; i++) {
        int a, b;
        cin >> a >> b;
        int result = calculateOperations(a, b);
        cout << result << endl;
    }

    return 0;
}

}
```
</details>


<details>
	<summary>JAVA</summary>
  
```java
import java.util.Scanner;

public class EqualSets {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        for (int i = 0; i < t; i++) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            int result = calculateOperations(a, b);
            System.out.println(result);
        }
    }

    public static int calculateOperations(int a, int b) {
        int diff = Math.abs(a - b);

        // Base cases
        if (diff == 0) {
            return 0;
        }
        if (diff == 1) {
            return 1;
        }

        // Approximate the value of n using the quadratic formula
        int n = (int)Math.sqrt(2 * diff);

        // Ensure the sum is at least equal to the difference
        while (n * (n + 1) / 2 < diff) {
            n++;
        }

        // Adjust for odd/even parity if necessary
        while ((n * (n + 1) / 2) % 2 != diff % 2) {
            n++;
        }

        return n;
    }
}
```
</details>

<!-- Fifth Question -->
# Spread Spree

<details>
<summary>Python</summary>
  
```python
t = int(input())
for i in range(t):
    n, m = map(int, input().split())
    if n > m:
        n, m = m, n
    MOD = 998244353 #given in the question
    time = m // 2 
    l = max(1, n - time)
    r = min(n, 1 + time)
    ans = (r * (r + 1) // 2) - ((l - 1) * l // 2)#sum of values from r to l
    ans = ans % MOD
    
    if m % 2 == 1:
        ans = (ans * (m + 1) // 2) % MOD#multiplying values of j as discussed in the idea
    else:
        ans = (ans * (m + 1)) % MOD
    
    print(ans)
```
</details>

<details>
<summary>Cpp</summary>

```cpp
#include <iostream>

using namespace std;

/**
 * @brief Calculates the answer for the given problem.
 *
 * @param n The first input value.
 * @param m The second input value.
 * @return int The calculated answer.
 */
int calculateAnswer(int n, int m) {
    if (n > m) {
        swap(n, m);
    }

    const int MOD = 998244353;
    int time = m / 2;
    int l = max(1, n - time);
    int r = min(n, 1 + time);
    int ans = (r * (r + 1) / 2) - ((l - 1) * l / 2);
    ans %= MOD;

    if (m % 2 == 1) {
        ans = (ans * (m + 1) / 2) % MOD;
    } else {
        ans = (ans * (m + 1)) % MOD;
    }

    return ans;
}

int main() {
    int t;
    cin >> t;

    for (int i = 0; i < t; i++) {
        int n, m;
        cin >> n >> m;
        int result = calculateAnswer(n, m);
        cout << result << endl;
    }

    return 0;
}
```
</details>

<details>
<summary>Java</summary>

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        for (int i = 0; i < t; i++) {
            int n = scanner.nextInt();
            int m = scanner.nextInt();
            int result = calculateAnswer(n, m);
            System.out.println(result);
        }
    }

    public static int calculateAnswer(int n, int m) {
        if (n > m) {
            int temp = n;
            n = m;
            m = temp;
        }

        final int MOD = 998244353;
        int time = m / 2;
        int l = Math.max(1, n - time);
        int r = Math.min(n, 1 + time);
        int ans = (r * (r + 1) / 2) - ((l - 1) * l / 2);
        ans %= MOD;

        if (m % 2 == 1) {
            ans = (ans * (m + 1) / 2) % MOD;
        } else {
            ans = (ans * (m + 1)) % MOD;
        }

        return ans;
    }
}
```
</details>