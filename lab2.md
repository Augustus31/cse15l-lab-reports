# Servers and Bugs

The code for `StringServer` is as follows:  
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String currStr = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
           String q = url.getQuery();
           String[] qs = q.split("=");
           if(qs[0].equals("s")){
            try{
                currStr += "\n" + qs[1];
                return currStr;
            }
            catch(Exception e){
                return e.getStackTrace().toString();
            }
                
           }
        }
        return "ERROR";
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
This server must be compiled with Server.java (the same file as the one used Lab 2) to work properly. Here are some examples of server queries and outputs:  
<br>
![image][sc1.png]  
In this image, I have entered the url `localhost:4000/add-message?s=juscelino` into my web browser. Since my server was launched on port 4000 on localhost, this sends the url to my server. This calls the `handleRequest` method with a parameter of the aforementioned url (packaged as a URI object in Java). The path is then extracted, and since it is `/add-message`, the code proceeds to extract the query (which begins after the `?`). Since valid queries are in the form `s=____`, the query is split using the `=`. If the first part of the query is indeed `s`, then the second part of the query is extracted and concatenated (along with a prepended newline) to the String `currStr`. `currStr` is the String that stores user input in this server, and was initialized to lambda (the empty String) when the server was launched. Finally, the (new) value of currStr is returned and printed on the webpage.  
<br>
![image][sc2.png]
In this image, I have entered the url `localhost:4000/add-message?s=kubitscheck` into my web browser. The same processes occur as outlined in the previous image, with one change: the value of currStr is changed from `\nJuscelino` to `\nJuscelino\nKubitscheck`. `Kubitscheck` is simply concatenated to the String, with a newline before it. The new value of currStr is returned and printed on the webpage.
<br><br><br>


