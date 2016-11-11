# CodeChallenge
Insight Code Challenge

//Code written in Java

import java.io.File;
import java.io.FileNotFoundException;
import java.util.ArrayList;
import java.util.Scanner;
import java.io.*;

public class PayMo {

    public static void main(String[] args) throws FileNotFoundException, IOException {
        

        ArrayList <A> data = new ArrayList <> ();
        ArrayList <A> payment = new ArrayList <> ();
        PrintWriter out = new PrintWriter ("output1.txt");
        
        try {
            Scanner input = new Scanner(new File("paymo_input.txt"));
            Scanner stream = new Scanner(new FileReader("stream_payment.txt"));

            while(input.hasNextLine()){
                String line = input.nextLine();
                String[] details = line.split(", ");
                String id1_input = details[1];
                String id2_input = details[2];
                A a = new A(id1_input,id2_input);
                data.add(a);
            }
            input.close();
            
            while(stream.hasNextLine()){
                String line2 = stream.nextLine();
                String[] details2 = line2.split(", ");
                String id1_stream = details2[1];
                String id2_stream = details2[2];
                A b = new A(id1_stream, id2_stream);
                payment.add(b);
            }
            stream.close();
            
        } catch(final FileNotFoundException ex) {
            System.err.println(ex);
        }

        class A {
            private final String id1_input;
            private final String id2_input;
    
            public A(String id1_input, String id2_input){
                this.id1_input = id1_input;
                this.id2_input = id2_input;
            }
        }
        
        for (int i = 0; i < payment.size(); i++){
            //feature 1
            if(data.contains(data.get(i))){
                out.println("trusted");
            } else {
                out.println("unverified");
            }
        }
            
    }
    
}
