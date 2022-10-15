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

### Bug 1 (in ArrayExamples.java)
* Failure-inducing input:
![1](https://user-images.githubusercontent.com/100378969/195950231-f52451f6-2281-4c9a-b300-d933dbb88b23.png)

* Symptom:
![2](https://user-images.githubusercontent.com/100378969/195950253-2238fc6f-c225-419c-a1e1-79cd1ced31b6.png)

* Bug:
this line of code modifies the values in the original array instead of newArray. Therefore, by the time it returns the new array, it has only been initialized but not changed.
```
arr[i] = newArr[arr.length - i - 1];
```
![3](https://user-images.githubusercontent.com/100378969/195951537-d72ad1cd-33d1-4090-ada4-ef5bae89c4f2.png)


* The connection between the symptom and the bug: The symptom shows that the first element in the result array is 0 but not 1. It indicates that possibly the methods fails to reverse the array, or maybe it doesn't modify the values after the array is initialized. Looking at the method code, I found that the method indeed fails to update the new array after it is initialized, which is a bug.

* Correction of the bug:
We should modify the variable newArray we just created, but not the original array. And finally we should return newArray.
![4](https://user-images.githubusercontent.com/100378969/195950270-089817ff-5aeb-432f-8981-a5a695b42090.png)


### Bug 2 (in ListExamples.java)

* Failure-inducing input:
![5](https://user-images.githubusercontent.com/100378969/195950298-0373866a-4d94-4bf3-830c-d39bf0ff5e69.png)

* Symptom:
![6](https://user-images.githubusercontent.com/100378969/195950324-9ab8d14c-68bd-4033-ac14-fba7b5ae5ed3.png)

* Bug: This method adds the selected string to the front continously, which makes the string list in the reverse order with the original string list.
![7](https://user-images.githubusercontent.com/100378969/195951517-b74d2c55-175d-459d-afb5-8e02a1392088.png)


* The connection between the symptom and the bug: the symptom tells us that the result arraylist is not as we expected. It indicates that there might be some element missing or in the different order as we expected. Looking back at the method code, I found that this method indeed add the element to the front of the arraylist each time, which results in an arraylist of string with reversed order.

* Correction of the bug:
We should add the selected string to the end of the list instead of the front of the list.
![8](https://user-images.githubusercontent.com/100378969/195950337-ae3d27a8-5db6-4ea6-a1e0-0184da264982.png)