## 문제
<div style="white-space: pre-wrap;">

두 수의 최소공배수(Least Common Multiple)란 입력된 두 수의 배수 중 공통이 되는 가장 작은 숫자를 의미합니다. 예를 들어 2와 7의 최소공배수는 14가 됩니다. 정의를 확장해서, n개의 수의 최소공배수는 n 개의 수들의 배수 중 공통이 되는 가장 작은 숫자가 됩니다. n개의 숫자를 담은 배열 arr이 입력되었을 때 이 수들의 최소공배수를 반환하는 함수, solution을 완성해 주세요.

</div>

### 제한사항

<pre>
arr은 길이 1이상, 15이하인 배열입니다.
arr의 원소는 100 이하인 자연수입니다.
</pre>

### 입출력 예
<pre>
arr	        result
[2,6,8,14]	168
[1,2,3]	    6
</pre>


## 답안
```java
import java.util.*;

class Solution {
    public int solution(int[] arr) {
        int lcm = arr[0];
        for (int i = 1; i < arr.length; i++) {
            // 첫 수부터 2개씩 비교하면서 최소공배수 계산
            lcm = getLCM(lcm, arr[i]);
        }
        return lcm;
    }
    
    // 최소공배수(LCM) 계산
    private int getLCM(int a, int b) {
        // 두 수의 최소공배수는 두 수의 곱을 최대공약수로 나눈 값
        return a * b / getGCD(a, b);
    }
    
    // 최대공약수(GCD) 계산
    private int getGCD(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }
}
```