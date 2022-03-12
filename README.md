# ButtonHandler
Arduino library to process button clicks, supporting many different event types.

This library reads the changes coming from a digital input connected to a push button and processes them into many different events that can easily be distinguised by the main program:

## Usage
Initialize the handler for each button with the desired pin number. By default, the pin is initialized using the INPUT_PULLUP configuration.

    ButtonHandler _test_button(8);

In the loop(), use the run() method to read the pin data and process it

    _test_button.run();
    
    
## Supported Events

Has the input changed side the last loop?

    bool changed()

Did the button went down on this loop?

    bool pressed()

Did the button went down recently and enough time has passed so we know is not a double press?

    bool singlePressed()

Did the button went down on this loop and again recently in a previous loop?

	 bool doublePressed()

Did the button went up on this loop?

	 bool released()

Was there a button click in this loop (button down -> button up) ?

	 bool clicked()

Was there a long button click in this loop (button down -> wait -> button up) ?

	 bool longClicked()

Was there a double button click in this loop (two button clicks in a short period)?

	 bool doubleClicked()

Was there a repeat event in this loop?
Repeats happen when the button is pressed and then periodically untill the button is released

	 bool repeat()
  

Is the button currently being held?

	 bool hold()

Is the button currently being held after a single button press and the double click timeout has passed?

	 bool singleHold()

Is the button currently being held after a double button press?

	 bool doubleHold()

Is the button currently being held for at least a second?

    bool longHold()

Set the current toggle value for the button

    void setToggle(bool value)

Get the current toggle value for the button
The values changes between true and false whenever the button is pressed

    bool checkToggle()
    
    
# Optional Customizations
These #defines can be changed in the ButtonHandler.h file of the library to change the timings used to calculate all the events processed. All of the values are set in ms.

Debounce time for the button (to filter out electric noise when the button state changes)

    #define DEBOUNCE_TIME 50

Minimum time for a click to be considered a long click

    #define LONG_CLICK_MIN_TIME 400

Minimum time for a hold event to start triggering

    #define HOLD_LONG_TIME 1000

Maximum time difference between two clicks for the second click to be considered a double click

    #define DOUBLE_CLICK_TIMEOUT 300

Time to wait before triggering the first repeat
    
    #define BUTTON_REPEAT_TRIGGER 250

Time to wait before triggering two repeats 

    #define BUTTON_REPEAT_PERIOD 100

Boolean state of the input pin when the button is pressed

    #define BUTTON_PRESSED false
