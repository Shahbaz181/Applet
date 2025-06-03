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
