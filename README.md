# ps04/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package assignmentFour;

import java.util.*;
import java.io.*;

/**
 * assignment04 
 * C202 
 * 3/26/2017
 * @author piaoxie
 */
public class assignment04 {

    /**
     *
     * @param args
     */
    public static void main(String[] args) {

        MyLinkedList[] list = new MyLinkedList[26];
        int compsfound = 0, wordsfound = 0, compsnotfound = 0, wordsnotfound = 0;
        int avgcompswordsfound = 0, avgcompswordsnotfound = 0;
        for (int i = 0; i < list.length; i++) {

            list[i] = new MyLinkedList();

        }

        File f = new File("random_dictionary.txt");

        String inputWord;

        try {

            Scanner in = new Scanner(f);

            while (in.hasNext()) {

                inputWord = in.next();

                inputWord = inputWord.toLowerCase();

                int i = (inputWord.charAt(0) - 97);

                list[i].addLast(inputWord);

            }

            System.out.println("Processing complete: ");

            in.close();

        } catch (IOException e) {

            System.out.println("Unable to read file");

        }

        File oliver = new File("oliver.txt");

        try {
            Scanner in = new Scanner(oliver);

            while (in.hasNext()) {

                inputWord = in.next();

                inputWord = inputWord.toLowerCase();
                if (Character.isLetter(inputWord.charAt(0))) {
                    int i = (inputWord.charAt(0) - 97);

                    if (list[i].contains(inputWord)) {
                        System.out.println("The list contains: " + inputWord);
                        wordsfound++;
                        compsfound += list[i].indexOf(inputWord);
                    } else {
                        System.out.println("The list does not contain: " + inputWord);
                        wordsnotfound++;
                        compsnotfound += list[i].size();
                    }
                }
            }

            System.out.println("Processing complete ");

            in.close();

        } catch (IOException e) {

            System.out.println("Unable to read file");

        }   
        
        System.out.println("-------------------------------");
        
        avgcompswordsfound = compsfound / wordsfound;// ( avg # of comps per word) 
        avgcompswordsnotfound = compsnotfound / wordsnotfound;//(avg # of comps per word not found)
                
        System.out.println("Average number of compaarisons for wors found: " + avgcompswordsfound);
        System.out.println("Average number of compaarisons for wors not found: " + avgcompswordsnotfound);
        
    }

}
