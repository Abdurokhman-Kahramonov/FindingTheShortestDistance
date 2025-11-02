# 🏪 Closest Shop Finder (Java Swing Project)

An interactive **Java Swing** application that displays a simple map with shop locations and allows users to **click anywhere on the map** to find the **nearest shop** based on Euclidean distance.  
Each shop is visualized with its logo, and user clicks appear as a marker icon.

---

## 🧭 Overview

When a user clicks on the map:
- The program converts the mouse click coordinates into a **Cartesian plane** centered on the window.  
- It then computes distances to all known shop coordinates.  
- The nearest shop’s name and its distance are shown at the top of the window.  

This project demonstrates GUI programming with Swing, event handling with `MouseListener`, image rendering, and 2D coordinate transformations.

---

## 🧩 Key Features

- 📍 Click anywhere to mark your location on the map.  
- 🧮 Automatically calculates the **closest shop**.  
- 🖼️ Displays shop logos (Korzinka, Havas, Makro).  
- 🧭 Real-time coordinate conversion from screen space to map space.  
- 🧠 Uses a `TreeSet` to efficiently find the nearest shop by distance.  

---

## 🧱 Technologies Used

- **Java 20**  
- **Swing** for GUI  
- **AWT** for 2D graphics  
- **Java Collections Framework** (`TreeSet`, `ArrayList`, `Comparator`)  
- **ImageIO** for loading images  
- **OOP principles** with encapsulated `Shop` class  

---

## 🗂️ Project Structure

```
src/
 └── Main/
      ├── Execute.java
      ├── Window.java
      ├── Shop.java
      ├── MousePositionExample.java
      └── ProjectFTCW.iml
```

### 1. `Execute.java`
Main entry point — simply creates a `Window` instance and displays it.

```java
public class Execute {
    public static void main(String[] args) {
        Window window = new Window();
        window.show();
    }
}
```

---

### 2. `Window.java`
The main GUI class — handles:
- Drawing background and shop icons.
- Capturing mouse clicks.
- Coordinate transformations.
- Calculating and displaying nearest shop info.

**Main Components**
- `JFrame` — main window.  
- `JPanel` — custom map drawing surface.  
- `MouseListener` — detects clicks and triggers recalculations.  
- `TreeSet<Shop>` — sorts shops by distance.  
- Helper functions:
  - `formulate()` — converts from screen to Cartesian coordinates.  
  - `deFormulate()` — converts back to screen coordinates.  
  - `findDistance()` — standard Euclidean formula.  

---

### 3. `Shop.java`
Encapsulates all shop-related data:
- `x`, `y` — coordinates in map space.  
- `name` — shop name.  
- `color` — marker color.  
- `image` — logo image.  
- `distanceFromX` — dynamically updated distance from clicked point.

```java
public class Shop {
    private int x, y;
    private String name;
    private Color color;
    private BufferedImage image;
    private double distanceFromX;
    // Getters, setters, and constructor
}
```

---

### 4. `MousePositionExample.java`
A small standalone demo showing how to track mouse coordinates and display a red circle at the clicked position. (Likely used during early testing of the main UI.)

---

## 🎨 How It Works

1. **Startup**
   - Loads background map (`img.png`) and shop logos.
   - Creates a panel and attaches mouse listener.

2. **Click Event**
   - Mouse coordinates are read and converted to Cartesian coordinates.
   - Each shop’s distance is computed using:
     \[
     \text{distance} = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}
     \]
   - The nearest shop is determined using a `TreeSet` sorted by distance.

3. **Drawing**
   - Background image and icons are drawn using `Graphics.drawImage()`.
   - The clicked location is drawn with a small icon (e.g., marker pin).
   - The label on top shows coordinates and the nearest shop.

---

## 🖼️ GUI Layout

```
+-----------------------------------------------------------+
| Coordinates: X=120, Y=-40  Closest: Korzinka  Dist: 132 m |
|-----------------------------------------------------------|
|                                                           |
|                     (background image)                    |
|     [Korzinka]                                   [Makro]  |
|                                                           |
|                  [Havas]                                  |
|                                                           |
|     (click marker)                                        |
|                                                           |
+-----------------------------------------------------------+
```

---

## 📁 Assets (image paths)

Default asset paths (used in code):

```text
C:\Users\<user>\IdeaProjects\ProjectFTCW\src\assets\img.png
C:\Users\<user>\IdeaProjects\ProjectFTCW\src\assets\img_1.png
C:\Users\<user>\IdeaProjects\ProjectFTCW\src\assets\img_2.png
C:\Users\<user>\IdeaProjects\ProjectFTCW\src\assets\img_3.png
C:\Users\<user>\IdeaProjects\ProjectFTCW\src\assets\img_4.png
```

You may replace these with your own image assets or relative paths for portability.

---

## ⚙️ Coordinate Conversion

- **Formulate (Screen → Cartesian):**
  ```
  xC = x - WIDTH/2
  yC = HEIGHT/2 - y
  ```

- **Deformulate (Cartesian → Screen):**
  ```
  xC = WIDTH/2 + x
  yC = HEIGHT/2 - y
  ```

---

## 🚀 Running the Application

### 1. Build
```bash
javac Main/*.java
```

### 2. Run
```bash
java Main.Execute
```

---

## 💡 Future Improvements

- Add user-friendly UI (icons for zoom, reset).  
- Display distances dynamically as mouse moves.  
- Use geographic coordinates or scale map to meters.  
- Save and load shop data from JSON or database.  
- Add multiple location markers and route visualization.

---

## 📜 License
Use, modify, and distribute freely for educational purposes.

---

## 👩‍💻 Development Quick Reference

- Java 20 / Maven or IntelliJ project setup.  
- Libraries:
  - `javax.swing` for GUI
  - `java.awt` for drawing and event handling
  - `java.util` collections for shop management
  - `javax.imageio` for image loading

---
