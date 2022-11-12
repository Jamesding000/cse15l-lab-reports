# Lab Report 4 - Week 7
## Part 1
### Changing the name of the start parameter and its uses to base

- `vim DocSearcher.java`

enter vim normal mode

<img width="561" alt="截屏2022-11-12 上午12 25 47" src="https://user-images.githubusercontent.com/100378969/201466114-83c3bb8b-124c-422f-b1cb-beb481b24d83.png">

- `/start`

- `<Enter>`

use `/` to search for a the keyword "start", and press enter


<img width="516" alt="截屏2022-11-12 上午12 26 36" src="https://user-images.githubusercontent.com/100378969/201466115-6418016f-8d19-4968-9288-1e04ddfaa854.png">



- `cgn`

use `cgn` to replace the current word

<img width="506" alt="截屏2022-11-12 上午12 27 29" src="https://user-images.githubusercontent.com/100378969/201466117-228e92f1-751d-4f51-94d4-d5b31985336e.png">


- `base`

type in the new variable name "base"


<img width="512" alt="截屏2022-11-12 上午12 28 00" src="https://user-images.githubusercontent.com/100378969/201466120-87dd45ac-94f3-4d14-b7f7-854e446874e8.png">



- `<Esc>`

click `<Esc>` to exit insert mode (back to normal mode)

<img width="481" alt="截屏2022-11-12 上午12 38 38" src="https://user-images.githubusercontent.com/100378969/201466246-932e7e2b-4209-41e4-9831-ffe67dbc0b42.png">


- `n`

click `n` to move the cursor to the next matching word

<img width="500" alt="截屏2022-11-12 上午12 28 55" src="https://user-images.githubusercontent.com/100378969/201466124-00f7ff6c-af13-464c-b433-86bd691954d6.png">


- `.`

click `.` to paste the word "base" here

<img width="506" alt="截屏2022-11-12 上午12 29 18" src="https://user-images.githubusercontent.com/100378969/201466127-41ee90da-2bec-47ff-95bc-7ffa018c6532.png">


- `n.`

repeat `n.` again to replace the next appearance of "start" to "base"

<img width="537" alt="截屏2022-11-12 上午12 29 45" src="https://user-images.githubusercontent.com/100378969/201466131-034bc5fb-aa87-42af-b4bd-57238e89bb1f.png">


- `wq:`

Since all of variables named "start" in this method have been replaced by "base", we now save our change and exit vim using `wq:`

<img width="471" alt="截屏2022-11-12 上午12 41 08" src="https://user-images.githubusercontent.com/100378969/201466319-89480eae-e480-480e-9489-1ad97800eb1d.png">

- `<Enter>`

Click `<Enter>` to exit vim

---

## Part 2

### Timing on 2 options
- Edit using vscode, and then `scp` to the remote computer : 72s

- Login ssh and edit the code there : 61s

### Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?

- I prefer to use vim to directly edit the code there. Because after I become more familiar with the vim operations, I found it totally possible to edit the code using vim as effeciently as using vscode. Moreover, in this way, if the code doesn't work as I expected, I can re-open the code using vim and edit it again without copying the code again. 

### What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

- I think most of the time, directly editting the code on the remote computer using vim is better. Because oftentimes, after we copied our code to the remote computer and run the program there, we will probably encounter some unexpected behavior (because its common to have bugs in our code). Then this happens, we may need to modifty the code, and re-run it several times until it works correctly. If we use `scp` everytime we make some change to the code, it'll be extremely time consuming. So directly editing the code on the remote computer is a desired choice. 