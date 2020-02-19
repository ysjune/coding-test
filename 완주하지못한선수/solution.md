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

