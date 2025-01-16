Array: Store multiple values in a single varibale
```Java
public class Main {
	public static void main(String[] args) {
		String[] cars = {"Camaaro", "Corvette", "Tesla"};
		
		cars[0] = "Mustang";
		
		System.out.println(cars[1]);
		
		String[] letters = new String[3];
		letters[0] = "A";
		letters[1] = "B";
		letters[2] = "C";
		
		for(int i=0; i<letters.length; i++) {
			System.out.println(letters[i]);
		}
	}
}
```

# 2D Arrays
An array of arrays

```Java
public class Main {
	public static void main(String[] args) {
		String[][] cars = new String[3][3];
		
		/*
		String[][] cars = {
						   {"Camero", "Corvette", "Silverado"},
						   {"Mustang", "Ranger", "F-150"},
						   {"Ferrari", "Lambo", "Tesla"}
						  };
		*/
		cars[0][0] = "Camero";
		cars[0][1] = "Corvette";
		cars[0][2] = "Silverado";
		cars[1][0] = "Mustang";
		cars[1][1] = "Ranger";
		cars[1][2] = "F-150";
		cars[2][0] = "Ferrari";
		cars[2][1] = "Lambo";
		cars[2][2] = "Tesla";
		
		for(int i=0; i<cars.length; i++) {
			System.out.println();
			for(int j=0; j<cars[i].length; j++) {
				System.out.print(cars[i][j] + " ");
			}
		}
	}
}
```