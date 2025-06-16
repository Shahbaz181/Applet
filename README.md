swing...11

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MouseAdapterExample extends JFrame {
    String message = "";
    int x = 0, y = 0;
    public MouseAdapterExample() {
        setTitle("Mouse Adapter Example");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setBackground(Color.white);
        // Add MouseAdapter to the content pane
        addMouseListener(new MyMouseAdapter());
        // Make the frame visible
        setVisible(true);
    }
    public void paint(Graphics g) {
        super.paint(g); // clear previous drawings
        g.drawString(message, x, y);
    }
    class MyMouseAdapter extends MouseAdapter {
        public void mouseClicked(MouseEvent e) {
            x = e.getX();
            y = e.getY();
            message = "Mouse Clicked at (" + x + ", " + y + ")";
            repaint();
        }
    }
    public static void main(String[] args) {
        new MouseAdapterExample();
    }
}



applet....11


import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

/* <applet code="MouseAdapterExample" width=400 height=300></applet> */

public class MouseAdapterExample extends Applet {
 String message = "";
 int x = 0, y = 0;
 public void init() {
 setBackground(Color.white);
 // Attach custom mouse adapter
 addMouseListener(new MyMouseAdapter());
 }
 public void paint(Graphics g) {
 g.drawString(message, x, y);
 }
 // Custom adapter class
 class MyMouseAdapter extends MouseAdapter {
 public void mouseClicked(MouseEvent e) {
 x = e.getX();
 y = e.getY();
 message = "Mouse Clicked at (" + x + ", " + y + ")";
 repaint();
  }
 }
}

1. Save as `MouseAdapterExample.java`

2. Compile: `javac MouseAdapterExample.java`

3. Run with: `appletviewer MouseAdapterExample.java



Swing 1728


import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MouseKeySwingExample extends JPanel implements MouseListener,
    MouseMotionListener, KeyListener {
    String message = "";
    int mouseX = 0, mouseY = 0;

    public MouseKeySwingExample() {
        addMouseListener(this);
        addMouseMotionListener(this);
        addKeyListener(this);
        setBackground(Color.LIGHT_GRAY);
        setFocusable(true); // Important for key events
    }

    @Override
    public void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.drawString(message, mouseX, mouseY);
    }

    // MouseListener methods
    public void mouseClicked(MouseEvent e) {
        message = "Mouse Clicked";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseEntered(MouseEvent e) {
        message = "Mouse Entered";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseExited(MouseEvent e) {
        message = "Mouse Exited";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mousePressed(MouseEvent e) {
        message = "Mouse Pressed";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseReleased(MouseEvent e) {
        message = "Mouse Released";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    // MouseMotionListener methods
    public void mouseDragged(MouseEvent e) {
        message = "Mouse Dragged";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseMoved(MouseEvent e) {
        message = "Mouse Moved";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    // KeyListener methods
    public void keyPressed(KeyEvent e) {
        message = "Key Pressed: " + e.getKeyChar();
        repaint();
    }

    public void keyReleased(KeyEvent e) {
        message = "Key Released: " + e.getKeyChar();
        repaint();
    }

    public void keyTyped(KeyEvent e) {
        message = "Key Typed: " + e.getKeyChar();
        repaint();
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Mouse and Key Event Example");
        MouseKeySwingExample panel = new MouseKeySwingExample();
        frame.add(panel);
        frame.setSize(400, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}



applet 1728

import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

/* <applet code="MouseKeyApplet" width=400 height=300></applet> */

public class MouseKeyApplet extends Applet implements MouseListener, MouseMotionListener, KeyListener {

    String message = "";
    int mouseX = 0, mouseY = 0;

    public void init() {
        addMouseListener(this);
        addMouseMotionListener(this);
        addKeyListener(this);

        setBackground(Color.lightGray);
        setFocusable(true);  // Enables keyboard focus
        requestFocus();      // Requests focus on load
    }

    public void paint(Graphics g) {
        g.drawString(message, mouseX, mouseY);
    }

    // MouseListener methods
    public void mouseClicked(MouseEvent e) {
        message = "Mouse Clicked";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mousePressed(MouseEvent e) {
        message = "Mouse Pressed";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseReleased(MouseEvent e) {
        message = "Mouse Released";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseEntered(MouseEvent e) {
        message = "Mouse Entered";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseExited(MouseEvent e) {
        message = "Mouse Exited";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    // MouseMotionListener methods
    public void mouseDragged(MouseEvent e) {
        message = "Mouse Dragged";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    public void mouseMoved(MouseEvent e) {
        message = "Mouse Moved";
        mouseX = e.getX();
        mouseY = e.getY();
        repaint();
    }

    // KeyListener methods
    public void keyPressed(KeyEvent e) {
        message = "Key Pressed: " + e.getKeyChar();
        repaint();
    }

    public void keyReleased(KeyEvent e) {
        message = "Key Released: " + e.getKeyChar();
        repaint();
    }

    public void keyTyped(KeyEvent e) {
        message = "Key Typed: " + e.getKeyChar();
        repaint();
    }
}

To Run the Applet

1. Save the file as `MouseKeyApplet.java`.
2. Compile: `javac MouseKeyApplet.java`
3. Run using an applet viewer:appletviewer MouseKeyApplet.java

