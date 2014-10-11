---
layout: default
title: jMonkeyEngine Beginner's Guide
---

# jMonkeyEngine 3 Tutorial (1) - Hello SimpleApplication

Previous: [Installing JME3](/wiki/jme3#installing_jmonkeyengine_3),
Next: Hello Node

**Prerequisites:** This tutorial assumes that you have [downloaded the jMonkeyEngine SDK](http://jmonkeyengine.org/wiki/doku.php/).

In this tutorial series, we assume that you use the jMonkeyEngine [SDK]. As an intermediate or advanced Java developer, you will quickly see that, in general, you can develop jMonkeyEngine code in any integrated development environment (NetBeans IDE, Eclipse, IntelliJ) or even from the [command line](wiki/jme3/simpleapplication_from_the_commandline). 

OK, let's get ready to create our first jMonkeyEngine3 application.

## Create a Project

In the jMonkeyEngine SDK: 

 - Choose File->New Project... from the main menu.
 - In the New Project wizard, select the template JME3->Basic Game. Click Next. 
   - Specify a project name, e.g. "HelloWorldTutorial"
   - Specify a path where to store your new project, e.g. a ''jMonkeyProjects'' directory in your home directory.
 - Click Finish. 

If you have questions, read more about [:sdk:Project Creation) here.

<note tip>We recommend to go through the steps yourself, as described in the tutorials. Alternatively, you can create a project based on the [JmeTests](/wiki/sdk/sample_code) template in the jMonkeyEngine SDK. It will create a project that already contains the ''jme3test.helloworld'' samples (and many others). For example, you can use the JmeTests project to verify whether you got the solution right.</note>

## Extend SimpleApplication

For this tutorial, you want to create a ''jme3test.helloworld'' package in your project, and create a file ''HelloJME3.java'' in it. 

In the jMonkeyEngine SDK: 
  - Right-click the Source Packages node of your project.
  - Choose New...->Java Class to create a new file.
  - Enter the class name: ''HelloJME3''
  - Enter the package name: ''jme3test.helloworld''. 
  - Click Finish.
The SDK creates the file HelloJME3.java for you.

## Sample Code

Replace the contents of the HelloJME3.java file with the following code:

<code java>
package jme3test.helloworld;

import com.jme3.app.SimpleApplication;
import com.jme3.material.Material;
import com.jme3.math.Vector3f;
import com.jme3.scene.Geometry;
import com.jme3.scene.shape.Box;
import com.jme3.math.ColorRGBA;

### Sample 1 - how to get started with the most simple JME 3 application.

Display a blue 3D cube and view from all sides by moving the mouse and pressing the WASD keys.

```java
public class HelloJME3 extends SimpleApplication {

    public static void main(String[] args){
        HelloJME3 app = new HelloJME3();
        app.start(); // start the game
    }
    
    @Override
    public void simpleInitApp() {
        Box b = new Box(1, 1, 1); // create cube shape
        Geometry geom = new Geometry("Box", b);  // create cube geometry from the shape
        Material mat = new Material(assetManager,
          "Common/MatDefs/Misc/Unshaded.j3md");  // create a simple material
        mat.setColor("Color", ColorRGBA.Blue);   // set color of material to blue
        geom.setMaterial(mat);                   // set the cube's material
        rootNode.attachChild(geom);              // make the cube appear in the scene
    }
}
```

Right-click the HelloJME3 class and choose Run. If a jME3 settings dialog pops up, confirm the default settings.

  - You should see a simple window displaying a 3D cube.
  - Press the WASD keys and move the mouse to navigate around.
  - Look at the FPS text and object count information in the bottom left. 

You will use this information during development, and you will remove it for the release. (To read the numbers correctly, consider that the 14 lines of text counts as 14 objects with 914 vertices.)

  - Press Escape to close the application.

Congratulations! Now let's find out how it works!

## Understanding the Code

The code above has initialized the scene, and started the application.

### Start the SimpleApplication

Look at the first line. Your HelloJME3.java class extends `com.jme3.app.SimpleApplication`.

```java
public class HelloJME3 extends SimpleApplication {
  // your code...
}
```

Every JME3 game is an instance of the `com.jme3.app.SimpleApplication` class. The SimpleApplication class is the simplest example of an application: It manages a 3D scene graph, checks for user input, updates the game state, and automatically draws the scene to the screen. These are the core features of a game engine. You extend this simple application and customize it to create your game.

You start every JME3 game from the main() method, as every standard Java application: 

  - Instantiate your ''SimpleApplication''-based class
  - Call the application's ''start()'' method to start the game engine. 

```java
    public static void main(String[] args){
        HelloJME3 app = new HelloJME3(); // instantiate the game
        app.start();                     // start the game!
    }
```

The `app.start();` line opens the application window. Let's learn how you put something into this window (the scene) next.

### Understanding the Terminology

^What you want to do^How you say that in JME3 terminology^
](You want to create a cube.](I create a Geometry with a 1x1x1 Box shape.](
](You want to use a blue color.](I create a Material with a blue Color property.](
](You want to colorize the cube blue.](I set the Material of the Box Geometry.](
](You want to add the cube to the scene.](I attach the Box Geometry to the rootNode.](
](You want the cube to appear in the center.](I create the Box at the origin = at ''Vector3f.ZERO''.](

If you are unfamiliar with the vocabulary, read more about [:jme3:the Scene Graph) here.

### Initialize the Scene

Look at rest of the code sample. The ''simpleInitApp()'' method is automatically called once at the beginning when the application starts. Every JME3 game must have this method. In the ''simpleInitApp()'' method, you load game objects before the game starts. 

```java
    public void simpleInitApp() {
       // your initialization code...
    }
```

The initialization code of a blue cube looks as follows:

```java
    public void simpleInitApp() {
        Box b = new Box(1, 1, 1); // create a 1x1x1 box shape
        Geometry geom = new Geometry("Box", b);  // create a cube geometry from the box shape
        Material mat = new Material(assetManager,
          "Common/MatDefs/Misc/Unshaded.j3md");  // create a simple material
        mat.setColor("Color", ColorRGBA.Blue);   // set color of material to blue
        geom.setMaterial(mat);                   // set the cube geometry 's material
        rootNode.attachChild(geom);              // make the cube geometry appear in the scene
    }
```
     
A typical JME3 game has the following initialization process:

  - You initialize game objects:
    * You create or load objects and position them.
    * You make objects appear in the scene by attaching them to the ''rootNode''.
    * **Examples:** Load player, terrain, sky, enemies, obstacles, ..., and place them in their start positions.
  - You initialize variables
    * You create variables to track the game state. 
    * You set variables to their start values. 
    * **Examples:** Set the ''score'' to 0, set ''health'' to 100%, ...
  - You initialize keys and mouse actions.
    * The following input bindings are pre-configured:
      * W,A,S,D keys -- Move around in the scene
      * Mouse movement and arrow keys -- Turn the camera
      * Escape key -- Quit the game
    * Define your own additional keys and mouse click actions.
    * **Examples:** Click to shoot, press Space to jump, ...

## Conclusion

You have learned that a SimpleApplication is a good starting point because it provides you with:

  * A `simpleInitApp()` method where you create objects.
  * A `rootNode` where you attach objects to make them appear in the scene.
  * Useful default input settings that you can use for navigation in the scene.

When developing a game application, you want to:

  - Initialize the game scene
  - Trigger game actions 
  - Respond to user input.

The now following tutorials teach how you accomplish these tasks with the jMonkeyEngine 3.

Continue with the [jme3:beginner:Hello Node) tutorial, where you learn more details about how to initialize the game world, also known as the scene graph.

----

See also: 

  * [http://jmonkeyengine.org/wiki/doku.php/](Install the jMonkeyEngine)
  * [:jme3:SimpleApplication From the Commandline)
  * [:sdk:Project Creation](Create a JME3 project).