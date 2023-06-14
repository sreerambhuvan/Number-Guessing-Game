
import javax.swing.*;




import java.awt.Color;
import java.awt.Dimension;



import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.UIManager;
import javax.swing.JLabel;
import java.awt.Font;
import javax.swing.SwingConstants;



public class cp{
    public static void main(String[] args) {
        JPanel panel = new JPanel();
        panel.setBackground(new Color(0, 0, 0));
        panel.setSize(new Dimension(300, 250));
        panel.setLayout(null);
        JLabel label = new JLabel("Welcome To the Game :), Guess between 1 and 100 ,Max Guesses:10");
        label.setForeground(new Color(250, 100, 100));
        label.setHorizontalAlignment(SwingConstants.LEFT);
        label.setFont(new Font("Italic", Font.BOLD, 12));
        label.setBounds(0, 0, 460, 30);
        panel.add(label);
        UIManager.put("OptionPane.minimumSize",new Dimension(460, 190));
        UIManager.put("OptionPane.background", Color.gray);
        UIManager.put("Panel.background", Color.lightGray);
        UIManager.put("Button.foreground", Color.black);
        UIManager.put("MenuItem.foreground", Color.green);

        UIManager.put("TextField.selectionForeground", Color.WHITE);
        int inp = (int) (Math.random()*100 + 1);
        int ans = 0;
        int count = 1;



        while (ans != inp)
        {
            String response = JOptionPane.showInputDialog(null,panel,
                    "Number Guessing game ",  JOptionPane.QUESTION_MESSAGE);
            ans = Integer.parseInt(response);
            if(count>10){
                JOptionPane.showMessageDialog(null,""+"Good Try, But you didnot win this game\n Good luck :) for the next one");
                break;
            }
            else{
                JOptionPane.showMessageDialog(null, ""+ Guess(ans, inp, count));
            }
            count++;

        }
    }



    public static String Guess(int ans, int num, int count){
        if (ans<=0 || ans>100) {
            return " guess between 1 and 100";
        }
        else if (ans == num ){
            if(count<5){
                return "Wow Great! you have won this game within 5 guesses "+ count;
            }
            return "Correct!\nTotal Guesses: " + count;
        }
        else if (ans > num) {
            return " too high, guess again.\nTry Number: " + count;
        }
        else if (ans < num) {
            return "too low, guess again.\nTry Number: " + count;
        }
        else {
            return "Your guess is wrong" + count;
        }
    }
}
