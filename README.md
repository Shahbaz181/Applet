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
