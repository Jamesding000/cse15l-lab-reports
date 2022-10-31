# Lab Report 3 - Week 5
## Command Line Option 1 :  `grep -i`
This command line option allow you to ignore the lower and upper case when searching for the lines containing the keyword in the file/files.


### Example 1


* Before testing this command line option, this is the output without using -i. Notice that only sentene with lower case "many" are found.

```
grep "many" technical/biomed/1468-6708-3-1.txt
```

<img width="657" alt="截屏2022-10-30 下午6 39 36" src="https://user-images.githubusercontent.com/100378969/198915222-0e13c512-0ab4-44c9-b484-893713679937.png">



* Then after using -i option, lines with the content "many", regardless of case, are found and displayed.

```
grep -i  "many" technical/biomed/1468-6708-3-1.txt
```

<img width="700" alt="截屏2022-10-30 下午6 39 10" src="https://user-images.githubusercontent.com/100378969/198915232-0763e185-fa94-468b-9b68-b50070a4218e.png">

### Example 2

* Without using `-i`, no line is found by `grep` because there's no line containg the word "MANY".

```
grep "MANY" technical/biomed/1468-6708-3-1.txt
```
* Using the `-i` option, we can get the same result as Example 1, because the keyword are essentially the same without consider cases.


```
grep "MANY" -i technical/biomed/1468-6708-3-1.txt
```
<img width="680" alt="截屏2022-10-30 下午6 59 10" src="https://user-images.githubusercontent.com/100378969/198916537-e57272fe-3aac-4389-95e1-c1fb504464e1.png">


### Example 3
* If we search for "eXceLlEnT" directly using `grep`, no line will be printed. However, after using `-i` option, we get all the line containing the word "excellent" regardless of cases.

```
grep -i "eXceLlEnT" technical/biomed/1468-6708-3-1.txt
```
<img width="715" alt="截屏2022-10-30 下午7 00 30" src="https://user-images.githubusercontent.com/100378969/198916546-b5351d3f-bd52-4be1-b9f4-7b1ac8d09154.png">

## Command Line Option 2 :  `grep -c`

### Example 1
* This command line option search print the number (count) of the lines containing the given keyword.

* Without using `-c`, `grep` will print out the 2 lines containing "many".

```
grep "many" technical/biomed/1468-6708-3-1.txt
```

<img width="657" alt="截屏2022-10-30 下午6 39 36" src="https://user-images.githubusercontent.com/100378969/198915222-0e13c512-0ab4-44c9-b484-893713679937.png">

* If we use `-c`, `grep` give us the count of the lines containing "many".

```
grep "many" -c technical/biomed/1468-6708-3-1.txt
```

<img width="673" alt="截屏2022-10-30 下午7 47 24" src="https://user-images.githubusercontent.com/100378969/198920583-4220a2b1-6bc7-4e13-979c-9eb9639eefe0.png">

### Example 2
* If we use `-i` and `-c` together, `grep` will give us the count (number) of lines containing "MANY" regardless of cases. From Option1 Example3, this would give us 3.

```
grep "many" -i -c technical/biomed/1468-6708-3-1.txt
```

<img width="689" alt="截屏2022-10-30 下午7 53 29" src="https://user-images.githubusercontent.com/100378969/198921430-d0e00583-cab9-458c-b056-64afaec66cc1.png">

### Example 3
* If we use `-c` to search for an non-existing keyword, instead of printing nothing, it will give us 0.

```
grep "eXceLeNt" -c technical/biomed/1468-6708-3-1.txt
```

<img width="704" alt="截屏2022-10-30 下午8 11 37" src="https://user-images.githubusercontent.com/100378969/198923708-9d0a6967-1d3b-4186-9147-7f2f7110d8dd.png">

## Command Line Option 3 :  `grep -v`
This command line option search for the lines that do not contain the given keyword. In order word, it will print out all the lines except those can be found using `grep`.

### Example 1

* If we use `grep -v`, it will print out all the lines that doesn't contain the given keyword "many".

```
grep -v "many" technical/biomed/1468-6708-3-1.txt
```

<img width="709" alt="截屏2022-10-30 下午8 18 08" src="https://user-images.githubusercontent.com/100378969/198924191-073de13d-d300-4e92-89b2-4a939ef79cdb.png">

* If we use `-v` `-c` together, it will give us the number of lines that doesn't contain the keyword.

```
grep -v -c "many" technical/biomed/1468-6708-3-1.txt
```

<img width="714" alt="截屏2022-10-30 下午8 18 30" src="https://user-images.githubusercontent.com/100378969/198924304-d89c7533-675f-4367-afc9-267b62cf75a5.png">

### Example 2

* If we use `-i` `-v` `-c` together, it will give us the number of lines that doesn't contain the keyword regardless of cases.

```
grep -i -v -c "MANY" technical/biomed/1468-6708-3-1.txt
```

<img width="727" alt="截屏2022-10-30 下午8 19 19" src="https://user-images.githubusercontent.com/100378969/198924345-cfc7c6f6-162d-42be-9cab-7cea68e96235.png">

### Example 3

* If we use `-i` `-v` `-c` together on a non-exisiting keyword, it will give us the totol number of lines in this file.

```
grep -i -v -c "eXCeLeNt" technical/biomed/1468-6708-3-1.txt
```

<img width="746" alt="截屏2022-10-30 下午8 19 30" src="https://user-images.githubusercontent.com/100378969/198924396-354d3e20-cdbe-48fb-a190-f53f7a1f5a43.png">
