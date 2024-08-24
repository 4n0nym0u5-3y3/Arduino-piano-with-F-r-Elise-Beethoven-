# Arduino Piano with "Für Elise" Melody

This project is an Arduino-based mini piano that allows you to play different notes by pressing buttons. It also plays the melody of "Für Elise" by Ludwig van Beethoven when a specific button is pressed.

## Components Required

- Arduino UNO board 
- 8 push buttons
- 1 push button for starting the "Für Elise" melody
- 1 piezo buzzer
- Jumper wires
- Breadboard

## Pin Configuration

| Button | Arduino Pin |
|--------|-------------|
| Button 1 | 3 |
| Button 2 | 4 |
| Button 3 | 5 |
| Button 4 | 6 |
| Button 5 | 7 |
| Button 6 | 8 |
| Button 7 | 9 |
| Button 8 | 2 |
| "Für Elise" Button | 10 |
| Buzzer | 13 |

## Code Explanation

The code consists of two main parts: 

### Setup

The `setup()` function initializes the serial communication and sets the mode of each pin (input or output). 

```cpp
void setup()
{
  Serial.begin(9600);
  
  pinMode(but1, INPUT);
  pinMode(but1, OUTPUT);
  pinMode(but2, INPUT);
  pinMode(but3, INPUT);
  pinMode(but4, INPUT);
  pinMode(but5, INPUT);
  pinMode(but6, INPUT);
  pinMode(but7, INPUT);
  pinMode(but8, INPUT);
  pinMode(but_p, INPUT);

  pinMode(buzzer, OUTPUT);
}
```

### Loop

The `loop()` function checks the state of each button. When a button is pressed, the corresponding tone is played on the buzzer. The "Für Elise" button triggers the full melody sequence.

```cpp
void loop()
{
  int b1 = digitalRead(but1);
  int b2 = digitalRead(but2);
  int b3 = digitalRead(but3);
  int b4 = digitalRead(but4);
  int b5 = digitalRead(but5);
  int b6 = digitalRead(but6);
  int b7 = digitalRead(but7);
  int b8 = digitalRead(but8);
  int b_p = digitalRead(but_p);

  if(b1 == 1){
    tone(buzzer, 261, 100); // C4
  }
  if(b2 == 1){
    tone(buzzer, 293, 100); // D4
  }
  if(b3 == 1){
    tone(buzzer, 329, 100); // E4
  }
  if(b4 == 1){
    tone(buzzer, 349, 100); // F4
  }
  if(b5 == 1){
    tone(buzzer, 392, 100); // G4
  }
  if(b6 == 1){
    tone(buzzer, 440, 100); // A4
  }
  if(b7 == 1){
    tone(buzzer, 493, 100); // B4
  }
  if(b8 == 1){
    tone(buzzer, 523, 100); // C5
  }
  
  if(b_p == HIGH){
    inizio(); // Plays the "Für Elise" melody
  }
  delay(10);
}
```

### Melody Function

The `inizio()` function contains the sequence of tones and delays that reproduce the "Für Elise" melody.

```cpp
void inizio(){
    tone(buzzer, 659); //mi
    delay(300);
    tone(buzzer, 622);
    delay(300);
    tone(buzzer, 659);
    // Additional tones and delays follow...
}
```

## Usage

1. Connect the components as per the pin configuration.
2. Upload the code to the Arduino board.
3. Press the buttons to play different notes.
4. Press the "Für Elise" button to hear the melody.

## Notes

- Ensure that the connections are secure to avoid any issues with button presses or sound.
- You can modify the tones or add new melodies by updating the `inizio()` function.
