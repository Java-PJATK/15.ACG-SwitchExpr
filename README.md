# 15.ACG-SwitchExpr

Another kind of switch is the so-called switch expression. It has been available since Java 14. This is an expression, which means that the switch as a whole has a value. Therefore, each arm of the switch expression must itself be an expression, i.e., have a value (of the same type, or at least the types must be convertible to one common type). It can be just an expression, or a block ending with `yield value` – then the value indicated after the `yield` statement will be the value of the corresponding arm. Since the switch expression must have a value, it has to be exhaustive, i.e., for all possible values, there must be a matching switch label. For integral types and Strings, the number of possible values is practically infinite, so there is no way to avoid the default arm, as shown in the example below:

## Listing 15 ACG-SwitchExpr/SwitchExpr.java Page 35

```java
public class SwitchExpr {
    public static void main(String[] args) {
        int i = 7;
        var res = switch (i) {
            case 1, 2, 3 -> "First quarter";
            case 4, 5, 6 -> "Second quarter";
            case 7, 8, 9 -> {
                System.out.println("And here a block...");
                System.out.println("still we need a value...");
                yield "Third quarter";
            }
            case 10, 11, 12 -> "Fourth quarter";
            // must be exhaustive
            default -> "Something wrong";
        };
        System.out.println("res = " + res);
    }
}
```
