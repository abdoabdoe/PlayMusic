📖 Java Audio Player Documentation
1️⃣ Overview
This Java program allows users to play, stop, reset, and quit a .wav audio file using the Java Sound API (javax.sound.sampled).

🔹 The user provides the file path to a .wav file.
🔹 The program loads the file and plays it using Clip.
🔹 The user can control playback with simple commands (P, S, R, Q).

2️⃣ Technologies Used
Java SE (JDK 8+)
javax.sound.sampled package for handling audio
java.util.Scanner for user input
java.io.File for file handling
3️⃣ How It Works
Step 1: Get User Input for File Path
java
Copy
Edit
Scanner input = new Scanner(System.in);
System.out.println("Put the path of your song ");
music = input.nextLine();
String filePath = music;
File file = new File(filePath);
✅ User enters the full path of the .wav file.
✅ The program creates a File object to check if the file exists.

Step 2: Load and Play the Audio File
java
Copy
Edit
try(Scanner play = new Scanner(System.in); AudioInputStream audioStream = AudioSystem.getAudioInputStream(file)) {
    Clip clip = AudioSystem.getClip();
    clip.open(audioStream);
✅ The program loads the audio file using AudioInputStream.
✅ It opens the file using Clip.

Step 3: User Controls Playback
java
Copy
Edit
while(!response.equals("Q")) {
    System.out.println("P = Play");
    System.out.println("S = Stop");
    System.out.println("R = Reset");
    System.out.println("Q = Quit");
    System.out.println("Enter your choice ");
    response = play.next().toUpperCase();

    switch (response) {
        case "P" -> clip.start();
        case "S" -> clip.stop();
        case "R" -> clip.setMicrosecondPosition(0);
        case "Q" -> clip.close();
        default -> System.out.println("Invalid Choice");
    }
}
✅ The while loop runs until the user enters Q (Quit).
✅ Commands:

"P" → Plays the song
"S" → Stops playback
"R" → Resets the song to the beginning
"Q" → Closes the audio clip
Step 4: Handle Errors
java
Copy
Edit
catch (FileNotFoundException e) {
    System.out.println("Could not locate file");
} catch(IOException e) {
    System.out.println("Something went wrong");
} catch (UnsupportedAudioFileException e) {
    System.out.println("Audio file is not supported");
} catch (LineUnavailableException e) {
    System.out.println("Unable to access audio resource");
}
✅ Exceptions are handled to prevent crashes:

FileNotFoundException → If the file does not exist
IOException → If there's an input/output issue
UnsupportedAudioFileException → If the file is not a valid .wav file
LineUnavailableException → If the system cannot play audio
4️⃣ Example Usage
📌 User Input
mathematica
Copy
Edit
Put the path of your song
C:\Users\admin\Music\song.wav
📌 Program Output
makefile
Copy
Edit
P = Play
S = Stop
R = Reset
Q = Quit
Enter your choice:
📌 User Commands
less
Copy
Edit
P   // Plays the song
S   // Stops playback
R   // Resets to the start
Q   // Quits the program
5️⃣ Possible Enhancements
✅ Add MP3 support using JLayer (Javazoom).
✅ Show song duration and playback time.
✅ Loop the song automatically instead of manual reset.
🎯 Conclusion
This Java audio player is a simple yet effective way to play .wav files using Java Sound API. 🚀
Would you like a GUI version with buttons instead of text input? I can help with that! 🎵🎛️
