# Java Audio Player 🎵

## Overview
This Java program allows users to **play, stop, reset, and quit** a `.wav` audio file using the **Java Sound API (`javax.sound.sampled`)**.

### Features
✅ Play `.wav` audio files  
✅ Stop and reset playback  
✅ Simple command-based user interaction  
✅ Error handling for missing or unsupported files  

## Technologies Used
- **Java SE (JDK 8+)**
- **`javax.sound.sampled`** for audio playback
- **`java.util.Scanner`** for user input
- **`java.io.File`** for file handling

## How It Works

### Step 1: Get User Input for File Path
```java
Scanner input = new Scanner(System.in);
System.out.println("Put the path of your song ");
String filePath = input.nextLine();
File file = new File(filePath);
```
✅ User enters the full path of the `.wav` file.  
✅ The program creates a `File` object to check if the file exists.  

---

### Step 2: Load and Play the Audio File
```java
try (Scanner play = new Scanner(System.in);
     AudioInputStream audioStream = AudioSystem.getAudioInputStream(file)) {
    
    Clip clip = AudioSystem.getClip();
    clip.open(audioStream);
```
✅ The program loads the audio file using `AudioInputStream`.  
✅ It opens the file using `Clip`.  

---

### Step 3: User Controls Playback
```java
while(!response.equals("Q")) {
    System.out.println("P = Play");
    System.out.println("S = Stop");
    System.out.println("R = Reset");
    System.out.println("Q = Quit");
    System.out.println("Enter your choice: ");
    response = play.next().toUpperCase();

    switch (response) {
        case "P" -> clip.start();
        case "S" -> clip.stop();
        case "R" -> clip.setMicrosecondPosition(0);
        case "Q" -> clip.close();
        default -> System.out.println("Invalid Choice");
    }
}
```
✅ The loop continues until the user enters `Q` (Quit).  
✅ **Available commands:**
- `P` → Play the song
- `S` → Stop playback
- `R` → Reset playback to the beginning
- `Q` → Quit the program

---

### Step 4: Handle Errors
```java
catch (FileNotFoundException e) {
    System.out.println("Could not locate file");
} catch(IOException e) {
    System.out.println("Something went wrong");
} catch (UnsupportedAudioFileException e) {
    System.out.println("Audio file is not supported");
} catch (LineUnavailableException e) {
    System.out.println("Unable to access audio resource");
}
```
✅ **Exceptions handled:**  
- **FileNotFoundException** → If the file does not exist
- **IOException** → If there is an input/output issue
- **UnsupportedAudioFileException** → If the file is not a valid `.wav` file
- **LineUnavailableException** → If the system cannot play the audio

---

## Example Usage
### **📌 User Input**
```
Put the path of your song
C:\Users\admin\Music\song.wav
```

### **📌 Program Output**
```
P = Play
S = Stop
R = Reset
Q = Quit
Enter your choice:
```

### **📌 User Commands**
```
P   // Plays the song
S   // Stops playback
R   // Resets to the start
Q   // Quits the program
```

---

## Future Enhancements 🚀
🔹 **Add MP3 support** using `JLayer` (Javazoom).  
🔹 **Show song duration and playback time**.  
🔹 **Create a GUI version with buttons instead of text input**.  

---

## Contributing 🛠️
Feel free to contribute to this project by submitting pull requests or reporting issues!

---

## License 📜
This project is open-source under the **MIT License**.

---

## Author ✍️
Developed by Abdelrahman Morgan (https://github.com/abdoabdoe)

---

