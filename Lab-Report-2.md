# Lab Report 2
---
> PART 1

- Code:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    
    String str = "";
    int lineCount = 0;

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return str;
            //return String.format("Number: %d", num);
        } else if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            if (query != null && query.startsWith("s=")){
                String message = query.substring(2);
                lineCount = lineCount +1;
                str += lineCount + ". " + message + "\n";
                return str;
                
            }
            return "400 Bad Request: Invalid query parameter!";
        } else {
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
- Add message `Hello`
  ![](addHello.jpg)
- Add message `How are you`
  ![](addHowareyou.jpg)
