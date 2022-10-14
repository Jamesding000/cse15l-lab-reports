# Lab Report 3
## Part 1

The code in SearchEngine.java is shown below:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class SearchEngineHandler implements URLHandler{
    // An arraylist of Strings that can be manipulated by
    // various requests.
    ArrayList<String> listOfWords = new ArrayList<>();

    public String handleRequest(URI url) {

        System.out.println("Path: " + url.getPath());

        if (url.getPath().equals("/")) {
            return "Current Word List : " +  listOfWords.toString();
        }

        else if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");

            if (parameters[0].equals("s")) {
                listOfWords.add(parameters[1]);
                return String.format("A new string (%s) is Added! There are %d strings in the word list", parameters[1], listOfWords.size());
            }

            return "404 Not Found!";
        }

        else if (url.getPath().contains("/search")) {

            String[] parameters = url.getQuery().split("=");

            if (parameters[0].equals("s")) {
                
                ArrayList<String> result = new ArrayList<>();

                String searchKey = parameters[1];

                for (String word : listOfWords) {
                    if (word.toLowerCase().contains(searchKey.toLowerCase())) {
                        
                        result.add(word);

                        System.out.println(word);
                    }
                }

                return "Search result : " + result.toString();
                
            }

            return "404 Not Found!";

        }

        else {
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new SearchEngineHandler());
    }
}

```

### The screenshots are shown below:

1. Open the server I've just created using SearchEngine.java
* handleRequest method is called
* the current url is passed in
* there's no changes in any feild variables.
![Open the server](https://user-images.githubusercontent.com/100378969/195945319-116e5976-11aa-49bf-9127-42542a192904.png)


2. Add the word "Apple" to the word list
* handleRequest method is called, the "add" functionality is used within the method
* the current url is passed in handleRequest method, and "s=Apple" serve as a keyword argument to the "Add" functionality.
* the feild listOfWords is changed because a new word "Apple" is added to the arraylist.
![Add Apple to sever](https://user-images.githubusercontent.com/100378969/195945345-03430d6f-953d-4625-8683-fdc23f390960.png)


3. Add the word "Pear" to the word list
* handleRequest method is called, the "add" functionality is used within the method
* the current url is passed in handleRequest method, and "s=Pear" serve as a keyword argument to the "Add" functionality.
* the feild listOfWords is changed because a new word "Pear" is added to the arraylist.
![Add Pear to server](https://user-images.githubusercontent.com/100378969/195945363-775b019f-14db-4b66-a5d5-b4ddf9f12aa6.png)


4. Check for the current word list by passing in no query
* handleRequest method is called
* the current url is passed in
* there's no changes in any feild variables.
![Check the current word list](https://user-images.githubusercontent.com/100378969/195945443-4690ff77-c625-47d5-ab88-eccef687b028.png)


5. Search for words containing "app"
* handleRequest method is called, the "search" functionality is used within the method
* the current url is passed in handleRequest method, and "s=app" serve as a keyword argument to the "Search" functionality.
* there's no changes in any feild variables.
![Search for words containing app](https://user-images.githubusercontent.com/100378969/195945421-0d9585ea-528c-42cb-a025-efcaf94e572c.png)


## Part 2


