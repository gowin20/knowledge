# Nested Classes

Created: Dec 30, 2020 1:07 PM
ID: 202012301307
Subject: Java
Type of Note: Info

Java allows for nesting of classes within other classes.

```java
class Outer {
	...
	class Nested {
		...
	}
}
```

[https://repl.it/@JuniLearning/AJ10-Nested-Classes#Classroom.java](https://repl.it/@JuniLearning/AJ10-Nested-Classes#Classroom.java)

The outer class contains the nested class

Two main types of nested class: static nested class, inner class

The outer class ALWAYS has full vision and knowledge of everything going on inside of the nested class, even if it's declared private

# Static Nested Classes

```java
public class Outer {
	private static int secret() {
		return 42;
	}

	public static final class Nested {
		//this class does NOT have access to members of the outer class
		//unless they are static.

		//work around this by saving a reference to the outer class object:
		private Outer outer;
		private void setOuter(Outer outer) {
			this.outer = outer;
		}
	}
}
```

Basically, regular classes which are nested for convenience

- Can be instantiated WITHOUT instantiating the outer class
- Can only access STATIC methods of the outer class without a reference
- In order to access public instance members of outer class, you need to have a reference to the outer class
- Can't EVER access private instance members of the outer class

So why do this?

- The static nested class can access ALL static members of the outer class, even if they're declared private

[https://repl.it/@JuniLearning/AJ10-Juni-Bakery-Starter](https://repl.it/@JuniLearning/AJ10-Juni-Bakery-Starter)

# Inner Classes

More typical of what we think of, when we imagine nested classes. These classes live entirely inside of the outer classes

- You can't create an inner class without first creating an outer class
- Have access to ALL members of the outer class, whether public private or static
- Cannot have static variables or methods, at all

Rule of thumb: The outer class **HAS-A** inner class