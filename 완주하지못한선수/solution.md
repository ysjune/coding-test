```java
import java.util.Arrays;

class Solution {
    public String solution(String[] participants, String[] completions) {
         
        Arrays.sort(participants);
        Arrays.sort(completions);

        int i;
        for (i = 0; i < completions.length; i++) {
            if(!participants[i].equalsIgnoreCase(completions[i])) {
                return participants[i];
            }
        }
        return participants[i];
    }
}
```



### 해쉬를 이용한 풀이

```java
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<>();
        for (String player : participant) hm.put(player, hm.getOrDefault(player, 0) + 1);
        for (String player : completion) hm.put(player, hm.get(player) - 1);

        for (String key : hm.keySet()) {
            if (hm.get(key) != 0){
                answer = key;
            }
        }
        return answer;
    }
}
```

