<!-- HEADER -->
<div align="center">
  <h1 align="center">Input Output</h1>
</div>

# 1. Input

## 1.1 Scanner
> The Scanner class is used to read user input in a Java program. It requires declaration within a program before the user of the program is prompted to input values.
> 
> IOException refers to any errors that a program may encounter that are related to the input or output of a Java program.
```shell
import java.util.Scanner;

public class InputScanner {
  public static void main(String[] args)  throws IOException {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter your name: ");
    String userName = input.next();
    System.out.printf("Hello %s! It's nice to meet you", userName);
  }
}
```

## 1.2 FileInputStream
```shell
import java.io.*;

public class InputStream {
  public static void main(String[] args) throws IOException {
    String path = "/home/dev/inputFile.txt";
    FileInputStream inputFile = new FileInputStream(path);
    int i = 0;    
    while((i = inputFile.read()) != -1) {    
      System.out.print((char)i);    
    }    
    inputFile.close();
  }
}
```

# 2. Output
```shell
import java.io.*;

public class OutputStream {
  public static void main(String[] args) throws IOException {
    FileOutputStream output = new FileOutputStream("output.txt");
    String outputText = "any msg";
    // Convert statement to bytes.
    output.write(outputText.getBytes());
    output.close();
  }
}
```
