import javax.swing.JOptionPane;
import javax.swing.*;
import java.awt.*;

public class DotsAndBoxes extends JFrame {

    /**
     * The four following functions are used to check if a box is created with a line placement
     */

    public static boolean aboveCheck(int[][] cords, int cordOne, int cordTwo) {
        return cords[cordOne - 1][cordTwo - 1] == 1 && cords[cordOne - 1][cordTwo + 1] == 1 && cords[cordOne - 2][cordTwo] == 1;
    }

    public static boolean bottomCheck(int[][] cords, int cordOne, int cordTwo) {
        return cords[cordOne + 1][cordTwo - 1] == 1 && cords[cordOne + 1][cordTwo + 1] == 1 && cords[cordOne + 2][cordTwo] == 1;
    }

    public static boolean rightCheck(int[][] cords, int cordOne, int cordTwo) {
        return cords[cordOne - 1][cordTwo + 1] == 1 && cords[cordOne + 1][cordTwo + 1] == 1 && cords[cordOne][cordTwo + 2] == 1;
    }

    public static boolean leftCheck(int[][] cords, int cordOne, int cordTwo) {
        return cords[cordOne - 1][cordTwo - 1] == 1 && cords[cordOne + 1][cordTwo - 1] == 1 && cords[cordOne][cordTwo - 2] == 1;
    }

    final static int SIZE = 5;
    static Board b;
    static int[][] cords;

    /**
     * sets the pegs on the board
     */
    public static void setup() {
        for (int row = 0; row < SIZE; row++) {
            for (int col = 0; col < SIZE; col++) {
                b.putPeg("black", row, col);
            }
        }
    }

    public static void main(String[] args) {

        // Introduction to the player
        JOptionPane.showMessageDialog(null, "This is a two player game. To select a line to complete click in between any two dots. When the board is filled out, the player with more boxes filled out wins", "How to play", 1);
        b = new Board(SIZE, SIZE);
        cords = new int[150][150];
        setup();
        int turn = 1;
        int p1Points = 0;
        int p2Points = 0;
        int cnt = 0;

        while (true) {


            // Current turn and points
            if (turn % 2 == 1) {
                b.displayMessage("P1's turn \n" + " P1 points: " + p1Points + "  " + "P2 points: " + p2Points);
            } else {
                b.displayMessage("P2's turn \n" + " P1 points: " + p1Points + "  " + "P2 points: " + p2Points);
            }

            // Checks if game is over
            if(cnt == 40)
            {
                if(p1Points == p2Points) {
                    JOptionPane.showMessageDialog(null, "GAME OVER: TIE", "Game Over", 1);
                }
                else if(p1Points > p2Points) {
                    JOptionPane.showMessageDialog(null, "GAME OVER: Player 1 wins", "Game Over", 1);
                }
                else {
                    JOptionPane.showMessageDialog(null, "GAME OVER: Player 2 wins", "Game Over", 1);
                }

            }

            Coordinate x = b.getClick(); // Keeps asking for the users click

            /**
             * creates a marking system for every row on grid
             */

            for (int cordOne = 0, rowOne = 0, LabelBoundsY = 70, clickCheckY = 45; cordOne <= 8; cordOne += 2, LabelBoundsY += 60, clickCheckY += 60, rowOne += 1) {
                for (int i = 60, j = 105, cordTwo = 1, colTwo = 0, LabelBoundsX = 70; i <= 240; i += 60, j += 60, cordTwo += 2, colTwo += 1, LabelBoundsX += 60) {
                    if (x.getRow() >= clickCheckY && x.getRow() <= clickCheckY + 10 && x.getCol() >= i && x.getCol() <= j) {
                        if (cords[cordOne][cordTwo] == 1) {
                            continue;
                        } else {
                            b.drawLine(rowOne, colTwo, rowOne, colTwo + 1);
                            cnt++;
                            cords[cordOne][cordTwo] = 1;
                            System.out.println(cordOne + " " + cordTwo);

                            if (cordOne == 0) {
                                if (bottomCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else {
                                    turn++;
                                }
                            } else if (cordOne == 8) {
                                if (aboveCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY - 60, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY - 60, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else {
                                    turn++;
                                }
                            } else {
                                if (aboveCheck(cords, cordOne, cordTwo) && bottomCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        JLabel copy = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        copy.setBounds(LabelBoundsX, LabelBoundsY - 60, 50, 20);
                                        b.add(label);
                                        b.add(copy);
                                        p1Points += 2;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        JLabel copy = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        copy.setBounds(LabelBoundsX, LabelBoundsY - 60, 50, 20);
                                        b.add(label);
                                        b.add(copy);
                                        p2Points += 2;
                                    }
                                } else if (aboveCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY - 60, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY - 60, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else if (bottomCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else {
                                    turn++;
                                }
                            }
                        }
                    }
                }
            }

            /**
             * creates a marking system for every column on grid
             */

            for (int cordTwo = 0, colTwo = 0, i = 49, LabelBoundsX = 70; cordTwo <= 8; cordTwo += 2, i += 60, LabelBoundsX += 60, colTwo += 1) {
                for (int j = 105, cordOne = 1, rowOne = 0, clickCheckY = 60, LabelBoundsY = 70; clickCheckY <= 240; rowOne += 1, j += 60, LabelBoundsY += 60, cordOne += 2, clickCheckY += 60) {
                    if (x.getRow() >= clickCheckY && x.getRow() <= j && x.getCol() >= i && x.getCol() <= i + 10) {
                        if (cords[cordOne][cordTwo] == 1) {
                        } else {
                            b.drawLine(rowOne, colTwo, rowOne + 1, colTwo);
                            cnt++;
                            cords[cordOne][cordTwo] = 1;
                            System.out.println(cordOne + " " + cordTwo);
                            if (cordTwo == 0) {
                                if (rightCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else {
                                    turn++;
                                }
                            } else if (cordTwo == 8) {
                                if (leftCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX-60, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX-60, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else {
                                    turn++;
                                }
                            } else {
                                if (rightCheck(cords, cordOne, cordTwo) && leftCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        JLabel copy = new JLabel("P1");
                                        label.setForeground(Color.red);
                                        copy.setForeground(Color.red);
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        copy.setBounds(LabelBoundsX-60, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        b.add(copy);
                                        p1Points += 2;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        JLabel copy = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        copy.setBounds(LabelBoundsX-60, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        b.add(copy);
                                        p2Points += 2;
                                    }
                                } else if (leftCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX-60, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX-60, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else if (rightCheck(cords, cordOne, cordTwo)) {
                                    if (turn % 2 == 1) {
                                        JLabel label = new JLabel("P1");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p1Points += 1;
                                    } else {
                                        JLabel label = new JLabel("P2");
                                        label.setBounds(LabelBoundsX, LabelBoundsY, 50, 20);
                                        b.add(label);
                                        p2Points += 1;
                                    }
                                } else {
                                    turn++;
                                }
                            }

                        }
                    }
                }
            }
        }
    }
}
