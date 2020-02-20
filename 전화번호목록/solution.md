```java
import java.util.Arrays;

public class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;

        Arrays.sort(phone_book);
        int size = phone_book.length;

        for (int i = 0; i < size; i++) {
            for (int j = 1; j < size; j++) {
                if (i == j) {
                    continue;
                }
                if (phone_book[j].startsWith(phone_book[i])) {
                    answer = false;
                }
                break;
            }
        }
        return answer;
    }
}
```

- break문의 위치를 보면 알 수 있듯, 코끼리 뒷걸음칠 쳐서 얻어걸린 느낌의 문제.. startWith 는 딱 문제보자마자 써야겠다고 생각했으나, 정작 푸는 시간에서 오래 걸린...



##### 다르게 해시를 써서 풀이된 것을 보면

```java
class Solution {
    public boolean solution(String[] phoneBook) {
       for(int i=0; i<phoneBook.length-1; i++) {
            for(int j=i+1; j<phoneBook.length; j++) {
                if(phoneBook[i].startsWith(phoneBook[j])) {return false;}
                if(phoneBook[j].startsWith(phoneBook[i])) {return false;}
            }
        }
        return true;
    }
}
```

