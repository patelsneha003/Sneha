package myprograms;

import java.util.Scanner;

public class BasicGrammar {
    public static void main(String args[]) throws Exception
    {
        String str=null;
        int counter=0;
        int noun=0,verb=0,preposition=0;
        Scanner S=new Scanner(System.in);
        System.out.print("Please enter a String:");
        str=S.nextLine();
        String words[]=str.split(" ");   //split("",limit);
        /* RULE-1 They can be lowercase or uppercase letters from a-s
          It also contains: space, ., !.*/
        for(int i=0;i<str.length();i++)
        {
        if(str.charAt(i)>='a'&&str.charAt(i)<='s'||str.charAt(i)>='A'&&str.charAt(i)<='S'||str.charAt	(i)=='!'||str.charAt(i)==' '||str.charAt(i)=='.')
            
            counter=0;
        else
        {
            counter=1;
            break;
        }
        }
        if(counter==0)
        System.out.print("Rule-1 Valid\n");
        else
        System.out.println("Rule-1 Invalid characters");
        
        
        /* RULE-2 Words more than 8 characters are not valid*/
        counter=0;
        if(str.contains(" "))
        {

                for(String s:words)
                {
                if(s.length()>8)
                {
                System.out.println("Rule-2 Word is too long "+s);
                counter=1;
                }
                }
            if(counter==0)
                System.out.println("Rule-2 valid");
        }
        else
            System.out.println("Rule-2 No space between sentence");
        
        
        //Rule-3 verbs must end with d, r or l
        for(String s:words)
        {
        if(s.length()==4||s.length()==5)
        {
            if(s.endsWith("d")||s.endsWith("r")||s.endsWith("l"))
            {    System.out.println("Rule-3 valid");
            }
            else
                System.out.println("Rule-3 Verb "+s+" not ending with d,r or l ");
        }
        }
        
        /*Rule-4 
        Sentences always start with uppercase letters.
        Sentences always end with a dot . or ! if it's the end of a paragraph.
        Rule 4: Sentences are a combination of at least one Verb, Preposition and Noun
        */
        counter=0;
        if(!Character.isUpperCase(str.charAt(0)))
            System.out.println("Rule-4 sentence not starting with capital letter");
        
        if(str.endsWith(".")||str.endsWith("!"))
            counter=0;
        else
            System.out.println("Rule-4 sentence not ending with . or !");
        words=str.split(" ");
        for(String s:words)
                {
                    if(s.length()<=8&&s.length()>=6)
                        preposition=1;

                   if(s.length()<=3&&s.length()>=1)
                        noun=1;

                     if(s.length()>=4&&s.length()<=5)
                        verb=1;        
                }
                if(noun==0)
                        System.out.println("Rule-4 no noun in the sentence ");
                if(verb==0)
                        System.out.println("Rule-4 no verb in the sentence");
                if(preposition==0)
                        System.out.println("Rule-4 no preposition in the sentence");
                if(noun==0&&verb==0&&preposition==0)
                        System.out.println("Rule-4 valid");
     
                
               //Rule-5 paragraph with upto 3 sentence each in new line
                counter=0;
               for(int i=0;i<str.length();i++)
               {
                   if(str.charAt(i)=='.')
                       counter++;
               }
                if(counter>2)
                    System.out.println("Rule-5 upto 3 sentences are allowed");
                else
                    System.out.println("Rule-5 valid");
               //Rule-6 paragraph ends with !
                
                if(!str.endsWith("!"))
                    System.out.println("Rule-6 paragraph not ending with !");
                else 
                    System.out.println("Rule-6 valid");
                
}
}
