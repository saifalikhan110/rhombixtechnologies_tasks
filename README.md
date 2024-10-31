# rhombixtechnologies_tasks
package com.word.counter;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class WordsCounter extends JFrame {

    public WordsCounter() {

        setTitle("Word Counter");
        setSize(500, 350);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);


        Font font = new Font("Arial", Font.BOLD, 16);


        final JTextArea textArea = new JTextArea();

        textArea.setFont(new Font("Arial", Font.PLAIN, 14));

        textArea.setBorder(BorderFactory.createEmptyBorder(10, 10, 10, 10));

        textArea.setLineWrap(true);
        
        textArea.setWrapStyleWord(true);

        JButton countButton = new JButton("Count Words");
        JButton clearButton = new JButton("Clear");

        final JLabel wordCountLabel = new JLabel("Word Count: 0");
        wordCountLabel.setFont(font);
        wordCountLabel.setHorizontalAlignment(SwingConstants.CENTER);
        wordCountLabel.setOpaque(true);
        wordCountLabel.setBackground(new Color(60, 130, 180));
        wordCountLabel.setForeground(Color.WHITE);
        wordCountLabel.setPreferredSize(new Dimension(500, 40));

        countButton.setFont(font);
        clearButton.setFont(font);
        countButton.setBackground(new Color(70, 160, 90));
        countButton.setForeground(Color.WHITE);
        clearButton.setBackground(new Color(160, 70, 70));
        clearButton.setForeground(Color.WHITE);


        JPanel buttonPanel = new JPanel();
        buttonPanel.setLayout(new FlowLayout(FlowLayout.CENTER, 20, 10));
        buttonPanel.add(countButton);
        buttonPanel.add(clearButton);
        buttonPanel.setBackground(new Color(230, 230, 230));

        setLayout(new BorderLayout());
        add(wordCountLabel, BorderLayout.NORTH);
        add(new JScrollPane(textArea), BorderLayout.CENTER);
        add(buttonPanel, BorderLayout.SOUTH);


        countButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String text = textArea.getText();
                int wordCount = text.isEmpty() ? 0 : text.trim().split("\\s+").length;
                wordCountLabel.setText("Word Count: " + wordCount);
            }
        });

        clearButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                textArea.setText("");
                wordCountLabel.setText("Word Count: 0");
            }
        });
    }





    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            WordsCounter app = new WordsCounter();
            app.setVisible(true);
        });
    }
}
