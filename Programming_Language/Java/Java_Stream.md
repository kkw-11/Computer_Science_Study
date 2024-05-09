Stream
- 

```Java
package stream;

import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> fruitsList = new ArrayList<String>();

        fruitsList.add("apple");
        fruitsList.add("banana");
        fruitsList.add("pear");
        fruitsList.add("grape");

        List<String> upperFruiltsList = fruitsList.stream().map(f -> f.toUpperCase()).collect(Collectors.toList());
        upperFruiltsList.stream().forEach(System.out :: println);
    }
}

```