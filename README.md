# DevOps Unit 1 Workshop

Welcome to the Unit 1 Workshop!
This `README.md` file will explain what you'll be doing in this workshop.
Start by downloading this repository to your computer. You can do this by clicking the green "Code" button and selecting "Download ZIP".
Once you have the ZIP file, extract it to a location of your choice.
Open the folder in Visual Studio Code, and you're ready to go! You can continue following the instructions in this file either inside Visual Studio Code, or on the repository page on GitHub - whichever suits you best.

## Primer Exercises
### Pre-flight checks
We're going to run through the technology and skills required to execute the main exercise. Don't worry: with only one exception, it's all stuff we've covered in the course so far already.
Let's start by returning to the terminal and getting back into the CLI headspace.

### Operating the terminal
- Open your terminal (Terminal.app on Mac, Powershell on Windows, or your favourite terminal emulator).
> Corporate restrictions, or other technical issues? Follow this command and the rest of the workshop inside an ACG cloud server, follow these instructions: [Setting up and using an ACG cloud server](ACG-instructions.md)
- Now we're going to go over the basics. 

### Scripts, Echo
- We can use the terminal to run programs (or commands). 
- The `cd` command is used to change the current directory.
    - Typing `cd ~` into the terminal and pressing enter will change the current directory to the user's home directory.
    - Navigate to the folder where you extracted the workshop repository.
    - Once there, you should be able to see the `README.md` file in the terminal by typing `ls` and pressing Enter.
    - You can also confirm it's the right file by looking at the contents - do this by typing `cat README.md` and pressing Enter.
- The `echo` command is used to output text to the terminal.
    - Typing `echo "Hello, World!"` into the terminal and pressing enter will output `Hello, World!` to the terminal.
- We type commands into the terminal and press Enter to execute them. But we can also save a series of commands to a file and execute them all at once. This is called a script.
- Create a new file called `hello.sh` in the terminal by typing `touch hello.sh` and pressing Enter.
- Open the file in Visual Studio Code by typing `code hello.sh` and pressing Enter.
    - Alternatively, you can take this opportunity to practice opening the file in a command-line text editor. On Mac, you can use `nano hello.sh` (or `vim`, if you know how to use it). On Windows, you can also use `nano` or `vim`, but you'll need to install it first.
- Add the following content to the file:
    ```bash
    echo "Hello, World!"
    ```
- Save the file.
- Now, in the terminal, assuming you're still in the same directory as the file, you can run the script by passing it to the `bash` program. Do this by typing `bash hello.sh` and pressing Enter.
- You should see `Hello, World!` output to the terminal.
> If that didn't work, check you're in the right directory. Type `ls` to see that the contents of this directory are as you expect, and that `hello.sh` is there. If it's not, navigate to the right directory using `cd` and try again. You can use `pwd` to print the current directory.

### Variables, Interpolation
- We can use variables to store data in scripts.
- We can then use these variables in our scripts.
- Create a new file called `hello2.sh` in the terminal by typing `touch hello2.sh` and pressing Enter.
- Open the file in Visual Studio Code by typing `code hello2.sh` and pressing Enter.
- Add the following content to the file:
    ```bash
    greeting="Hello, World!"
    echo $greeting
    ```
- Save and run the script as before.
- You should see `Hello, World!` output to the terminal.
- We can also use the contents of variables alongside other text.
- Modify the script to look like this:
    ```bash
    greeting="Hello, World"
    echo "$greeting, I'm a script."
    ``` 
- Save and run the script.
- You should see `Hello, World, I'm a script.` output to the terminal.
- This is called interpolation. We're using the contents of the variable in a string.

### Arrays
- We can use arrays to store lists of data in scripts.
- We can then use these arrays in our scripts.
- Create a new file called `hello3.sh` in the terminal by typing `touch hello3.sh` and pressing Enter.
- Open the file in Visual Studio Code by typing `code hello3.sh` and pressing Enter.
- Add the following content to the file:
    ```bash
    greetings=("Hello, World" "Bonjour, le monde" "Hola, mundo" "Ciao, mondo")
    echo ${greetings[0]}
    echo ${greetings[1]}
    echo ${greetings[2]}
    echo ${greetings[3]}
    ```
- Save and run the script.
- You should see each of the greetings output to the terminal.
- We can also use a special syntax to get all the elements in the array.
- Modify the script to look like this:
    ```bash
    greetings=("Hello, World" "Bonjour, le monde" "Hola, mundo" "Ciao, mondo")
    echo ${greetings[@]}
    ```
- Save and run the script.
- You should see all the greetings output to the terminal - this time, all on the same line. This is because the `@` character expands to all the elements in the array, which are being `echo`ed all at once.
- We can further add to this syntax to get the number of elements in the array.
- Modify the script to look like this:
    ```bash
    greetings=("Hello, World" "Bonjour, le monde" "Hola, mundo" "Ciao, mondo")
    echo ${greetings[@]}
    echo "There are ${#greetings[@]} greetings in the array."
    ```
- Save and run the script.
- You should see all the greetings output to the terminal, followed by the number of greetings in the array.

### Arithmetic
- We can use the shell to perform arithmetic operations.
- We can use the `((` and `))` characters to perform arithmetic operations.
- Type `echo $(( 1 + 1 ))` into the terminal and press Enter.
- You should see `2` output to the terminal.
- We can also use variables in arithmetic operations.
- Type `number=5` into the terminal and press Enter.
- Type `echo $(( $number + 3 ))` into the terminal and press Enter.
- You should see `8` output to the terminal.
- Alongside `+`, we can also use `-`, `*`, and `/` for addition, subtraction, multiplication, and division.
- Type `echo $(( 10 / 3 ))` into the terminal and press Enter.
- You should see `3` output to the terminal.
- This is because the shell only performs integer division. It doesn't give us the remainder of the division.
- We can use the modulo operator to get the remainder of a division.
- Type `echo $(( 10 % 3 ))` into the terminal and press Enter.
- You should see `1` output to the terminal, because 10 divided by 3 is 3 with a remainder of 1.
- Similarly, `echo $(( 10 % 5 ))` will output `0`, because 10 divided by 5 is 2 with a remainder of 0.

### Random Numbers
- We can use a special variable in the shell to get a random number.
- Type `echo $RANDOM` into the terminal and press Enter.
- You should see a random number between 0 and 32767 output to the terminal.
- We can use this to generate random numbers in our scripts.
- It isn't always useful to have a number between 0 and 32767, so we can use the modulo operator to get a number in a smaller range.
- Type `echo $(( $RANDOM % 10 ))` into the terminal and press Enter.
- You should see a random number between 0 and 9 output to the terminal.
- This means that not only can we generate random numbers, but we can also generate random numbers in a specific range.
- If we choose a range of "the number of elements in an array", we can use this to randomly select an element from the array.
- Create a new file called `hello4.sh` in the terminal by typing `touch hello4.sh` and pressing Enter.
- Open the file in Visual Studio Code by typing `code hello4.sh` and pressing Enter.
- Add the following content to the file:
    ```bash
    greetings=("Hello, World" "Bonjour, le monde" "Hola, mundo" "Ciao, mondo")
    random_index=$(( $RANDOM % ${#greetings[@]} ))
    echo ${greetings[$random_index]}
    ```
- Save and run the script.
- You should see a random greeting output to the terminal.
- Run the script a few more times to see different greetings output to the terminal.

### Good To Go
We've refreshed ourselves on:
- Writing and running scripts
- Using variables
- Interpolating variables (using their contents in strings)
- Using arrays
- Performing arithmetic operations
- Generating random numbers
- Choosing random elements from an array

This is everything we need to know to complete the main exercise. Let's get started!

## Main Exercise
Your task today is to create an automated version of the Mad Libs game. Normally, in a Mad Libs game, you would be asked to fill in the blanks in a story, and then the story would be read back to you with your words in place of the blanks. 
Instead of manually filling in the blanks, you'll write a script that randomly selects words to fill in those blanks, before then presenting the complete story.

### Step 1: Create a script that outputs a story, with some "?" placeholders for words.
- Create a new file called `madlibs.sh`.
- Open the file in Visual Studio Code (or your preferred text editor).
- Write a script that outputs a story, with some placeholders for words. For example:
    ```bash
    echo "Once upon a time, in a land far, far away, there was a ? princess named ?."
    ```
- Save the file.
- Run the script to see the output.

### Step 2: Modify the script to generate random words, and fill in the blanks.
- Modify the script to generate random words to fill in the blanks.
- As a hint, you can use arrays to store lists of words, and then use the `$RANDOM` variable to generate a random index to select a word from the array. For the example above, you might use arrays like this:
    ```bash
    adjectives=("beautiful" "cruel" "kind" "wicked" "wise")
    names=("Alice" "Bob" "Charlie" "Diana" "Eve")
    ```
- Save and run the script to see the output.

### Step 3: Deploy your script to the cloud.
- Your script is great now, but it's only on your computer, and only you can see it (unless you share your screen with someone else). We need to deploy it to the cloud so that everyone can use it.
- Deploying scripts and applications to the cloud is a big part of a DevOps engineer's job. We'll cover this in more detail later in the course, but for now, we'll use a simple method to deploy our script.
- We've prepared a deployment script for you. It's called `deploy.sh`. You can use this script to deploy your `madlibs.sh` script to our server.
- Run the deployment script by typing `bash deploy.sh` into the terminal and pressing Enter.
- You should see a URL output to the terminal.
- Open the URL in your web browser to see your script running in the cloud.
- Press Refresh a few times to see different stories output to the screen.

### Step 4: Get feedback from someone
- You've just completed most of the DevOps cycle: you've written a script and deployed it. Now you need to get feedback on it so you can make it better.
- Gathering and effectively actioning feedback is an important part of the DevOps workflow, and so it is an important part of a DevOps Engineer's job. We'll also cover this in more detail later in the course, but for now, we'll satisfy ourselves with a simple approximation of gathering feedback, so we can practice closing the loop and finishing the DevOps cycle by actioning feedback in the form of a new version of the script.
- Share the URL with someone else in your breakout room, and gather feedback on the product (for this exercise, perhaps ask them to give you feedback on the story).
  - Maybe it was too short, or too long. Had too many different adjectives, or not enough. Maybe the story was great, but the words didn't quite fit the blanks. Or they fit the blanks too well, and there was nothing unexpected or interesting! You could adjust the word lists you use, or do quite a lot to change the impact of your story.
- If you need a different option for feedback, click this link to read some feedback we prepared earlier: [Feedback](feedback.md), then action it.
- Alternatively, you might have your own ideas. Maybe you want to create more fine grained categories of words, or draw different placeholders from different lists. If you have ideas of your own, feel free to incorporate them into your new version of the script.

### Step 5: Incorporate that feedback into a change, and deploy the change.
- Make a new version of your script that incorporates the feedback you received.
- Deploy the new version of your script to the cloud using the `deploy.sh` script.
- Open the URL in your web browser to see your new script running in the cloud.
- Press Refresh a few times to see different stories output to the screen.
- This is the DevOps cycle in action: you've written a script, deployed it, gathered feedback, and made a change. Now you're ready to gather feedback on the new version of the script, and make another change. This cycle can continue as long as you need it to.
- Importantly, you now have a sense for the minimum cycle time for your script. You know how long it takes to make an adjustment, deploy it, and gather feedback. This is a key metric for DevOps engineers, and it's worth reflecting on how long this cycle takes in the context of your work and team. Certainly it won't be as fast as you've just experienced, but could it be faster?

## Extensions
### Extension A: Dynamic stories from remote servers
Your script is currently generating stories from one or more template stories you've included in your script, alongside your word lists. This is great! But, you can add an extra element of dynamism to your script by having it fetch more story templates from a remote server. This way, you can lean on other peoples' creativity as well as your own. 

This is an example of integrating the systems you build with that of others, in order to combine strengths or interoperate with other data stores - this is an important aspect of DevOps.

Use the `curl` command to fetch a story template from a remote server, and then use that template to generate a story. 

Use this remote server: `https://ryi-do4_w1_stories.web.val.run/`

The stories it gives you will have the following kinds of placeholders, make sure you handle them: $ADJECTIVE, $NOUN, $VERB, $PLACE, $EMOTION, $PLURAL_NOUN, $SILLY_WORD, and $ADVERB.

### Extension B: 
We've built something fun today, but really all of the same setup and tools can be used to generate a wide range of things, including notices for when you need to leave home to get to the train station for your train, or a report on how many tickets and story points your teams have completed in the last sprint.

Use the `curl` command to fetch data from a remote server, and use `jq` to parse it. You can save the results to a variable, and interpolate them into a string to produce a very basic report.

Use this remote server: `https://ryi-do4_w1_tickets.web.val.run`

Use the "add" and "length" functions in `jq` to calculate the total number of story points completed in the last sprint, the total number of tickets completed in the last sprint, and maybe the average ticket size. Then, use these numbers to produce a report in your script.

