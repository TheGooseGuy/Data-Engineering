|data types|size|primitive/reference|value|
|----------|----|-------------------|-----|
|boolean|1 bit|primitive|true or false|
|byte|1byte|primitive|-128 to 127|
|short|2 bytes|primitive|-32,768 to 2,767|
|int|4 bytes|primitive|-2 billion to 2 billion|
|long|8 bytes|primitive|-9 quintillion to 9 quintillion|
|float|4 bytes|primitive|fractional number up to 6-7 digits, ex: 3.141592f|
|double|8 bytes|primitive|fractional number up to 15 digits|
|char|2 bytes|primitive|single character/letter/ASCII value, ex: 'f'|
|string|varies|reference|a sequence of characters, ex: "Hello, world"|


```Java
// To create a variable

int x = 123; // declaration + assignment = initialization
double y = 3.14;
boolean z = true;
char symbol = '@';
String name = "Goose";

system.out.print("My variable is: " + x);
```

# To Swap Two Variables
```Java
String x = "water";
String y = "acid";
String temp;

temp = x;
x = y
y = temp

System.out.println("x: " + x)
System.out.println("y: " + y)