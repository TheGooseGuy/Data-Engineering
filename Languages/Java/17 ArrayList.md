ArrayList is a resizeable array. (they only store reference data types)
```Java
public class Main {
	public static void main(String[] args) {
		ArrayList<String> food = new ArrayList<String>();
		
		food.add("Pizza");
		food.add("Hamburger");
		food.add("Hotdog");
		
		food.set(0, "Sushi");
		food.remove(2);
		
		
		for (int i=0; i<food.size(); i++) {
			System.out.println(food.get(i));
		}
	}
}
```

## 2D ArrayList
2D ArrayList is a dynamic list of lists (size changeable)

