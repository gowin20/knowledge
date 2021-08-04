# Generics

Created: Dec 30, 2020 1:08 PM
ID: 202012301308
Subject: [[old/Field Knowledge/Computer Science/Java]]
Type of Note: Info

[https://repl.it/@JuniLearning/AJ10-Node-Class](https://repl.it/@JuniLearning/AJ10-Node-Class)

Placeholders that let you wait to specify a type in java

Useful for cases in which you need lots of different types interacting together!

[https://repl.it/@JuniLearning/AJ10-Anything-Array](https://repl.it/@JuniLearning/AJ10-Anything-Array)

```java
/**A Node stores data of type "T" **/
public class Node<T>{
  private T data;
  public Node(T data){
    this.data = data;
  }
  public T get(){
    return data;
  }
  public void set(T data){
    this.data = data;
  }
  @Override
  public String toString(){
    return data.toString();
  }
}

public static void main(String[] args) {
    //Integer test
    Node<Integer> test1 = new Node<>(2);
    test1.set(3);
    System.out.println("\n"+test1);

    //String test
    Node<String> test2 = new Node<>("slam");
    test2.set(test2.get() + " dunk");
    System.out.println(test2);
}
```