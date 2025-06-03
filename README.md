import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MouseAdapterExample extends JPanel {
    String message = "";
    int x = 0, y = 0;

    public MouseAdapterExample() {
        setBackground(Color.WHITE);
        addMouseListener(new MyMouseAdapter());
        setFocusable(true);
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.drawString(message, x, y);
    }

    // Inner adapter class
    class MyMouseAdapter extends MouseAdapter {
        @Override
        public void mouseClicked(MouseEvent e) {
            x = e.getX();
            y = e.getY();
message = "Mouse Clicked at (" + x + ", " + y + ")";
            repaint();
        }
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Mouse Adapter Example");
        MouseAdapterExample panel = new MouseAdapterExample();
        frame.add(panel);
        frame.setSize(400, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}








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
