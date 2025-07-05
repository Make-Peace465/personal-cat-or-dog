Main objective
1. Create a timer that allows users to enter the minutes
2. Consist of the following components
    - A display screen to show the current time
        - The display screen involve 2 parts: a minute display and a second display 
    - An input field to let user to enter the number
    - A button for the user to start the timer
    - A button to stop the timer
    - A button to reset the timer

Setup:
1. Find the display element and store it in a variable called display
2. Find the start button element and store it in a variable called startBtn
3. Find the pause button element and store it in a variabla called pauseBtn
4. Find the reset button element and store it in a variable called resetBtn

Variables: 
let minutes = 25;
let seconds = 60;

function: 
A function called count() that do the following:

1. Update the screen in each second

//Put the variable inside the function to make it local
let minutesdisplay = minutes;
let secondsDisplay = seconds;

IF (seconds is smaller than 10):
    secondsDisplay is equal to "0" add seconds
END IF

IF (minutes is smaller than 10):
    minutesDisplay is equal to "0" add minutes
END IF

IF seconds is equal to 00:
    seconds = 60;
END IF

IF seconds is equal to 60:
    minutes -= 1;
    display.textContent = minutesDisplay + " : " + "00"
    
    ELSE:
    display.textContent = minutesDisplay + " : " + secondsDisplay
    END ELSE
END IF

IF (minutes is equal to 0) and (seconds is equal to 0):
    setTimeout(() => {clearInterval(timerId)});
    RETURN;
END IF

seconds -= 1;

Setinterval function to run the program every 1 second
1. Create a function variable called TimerID that runs every second, wrapping the above round() function

let timerID = setInterval(() => count(), 1000);


SetTimeout function to stop the program after 25 minutes
setTimeout(() => {clearInterval(timerID), 1510000})

A function to stop the program
- convert the current minutes and seconds into milliseconds
- Update the total Time
- stoping the program with setTimeout

FUNCTION stop() {
    totalTime = (minutes*60 + seconds) * 1000 + 1000;
    setTimeout(() => {clearInterval(timerId)}); 
}

A function to start the program

FUNCTION start() {
    let timerId = setInterval(() => count(), 1000);
}



Questions:
1. How to create a timer using Javascript?
    - Use setInterval() 
2. What are the steps involved in updating the screen?
    - Transfer the seconds into minutes
        - 25 minutes = 25 x 60 = 1500 seconds
        - Total milliseconds = 1500 x 1000 = 1500000

    - What do we want to do in each second?
        - Update the screen
            - Conditions
                - if it is doubled digit seconds, update the screen to the variable (Tackled)
                    - Example: 24:30
                - if it is singled digit seconds, update the screen to the variable plus a zero in front of it (Tackled)
                    - Example: 24: 09
                - if seconds become zero, decrease the minute by 1 and update the screen.
                    - seconds reset itself to 60 when it becomes 0
                    - When seconds = 60, the screen will show 00 instead of 60
                    IF seconds is equal to 60:
                        minutes -= 1;
                        display.textContent = minutes + ":" + "00";
                        seconds -= 1;
                    END IF
3. Can setInterval() be used in normal function instead of arrow function? 
4. Will arrow function runs a function automatically?
    - Set interval will run automatically
5. How to access a variable define inside a function outside of its scope? 
    - To access to a variable outside the current scope you want to, then you have to declare it outside this scope, or either pass it as parameter in your functions.
    - Define the variable outside the function scope and then assign it value inside the function

Debugging
1. The timer ran faster when the start button is clicked more than once


Usable codes:

//Code to show double digit on the screen (for second)
    if (seconds < 10) {
        secondsDisplay.textContent = "0" + seconds;
    } else {
        display.textContent = seconds;
    }
    seconds -= 1;

//Code to show double digit on the screen (for minutes)
    if (minutes < 10) {
        minutesDisplay.textContent = "0" + seconds;
    } else {
        display.textContent = seconds;
    }
    seconds -= 1;