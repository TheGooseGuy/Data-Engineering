Switch is a statement that allows a variable to be tested for equility against other values.

```Java
public class Main {
	public static void main(String[] args) {
		String day = "Pizza";
		
		switch(day) {
			case "Sunday": System.out.println("It is Sunday.");
			break;
			case "Monday": System.out.println("It is Monday.");
			break;
			case "Tuesday": System.out.println("It is Tuesday.");
			break;
			case "Wednesday": System.out.println("It is Wednesday.");
			break;
			case "Thursday": System.out.println("It is Thursday.");
			break;
			case "Friday": System.out.println("It is Friday.");
			break;
			case "Saturday": System.out.println("It is Saturday");
			break;
			default: System.out.println("That is not a day.");
		}
	}
}
```
Consider useing `switch` when there are a lot of `if` statements.