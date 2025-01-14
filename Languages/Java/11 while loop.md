`while` loop excutes a block of code as long as it's condition remains to be true.
```Java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		String name = "";
		while (name.isBlank()) {
			System.out.print("Enter your name: ");
			name = scanner.nextLine();
		}
		System.out.println("Hello " + name);
	}
}
```

Do loop is a variable of while loop.