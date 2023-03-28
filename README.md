# caesarcipher-implementation
ppt link: https://www.canva.com/design/DAFeNK2gaVs/aC6QnHntgEAiWn3Wt8_FUA/view?utm_content=DAFeNK2gaVs&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

package caesarcipher;
import java.util.Scanner;

public class caesarcipher 
{
	public static final String ALPHABET = "abcdefghijklmnopqrstuvwxyz";
	 
    public static String encrypt(String plaintext, int shifts)
    {
    	// Converting into lowercase completely
    	plaintext = plaintext.toLowerCase();    
    	
        String ciphertext = "";
        for (int i = 0; i < plaintext.length(); i++)
        {
            int ptvalue = ALPHABET.indexOf(plaintext.charAt(i));
            int ctvalue = (ptvalue + shifts) % 26;
            char ctreplacevalue = ALPHABET.charAt(ctvalue);
            ciphertext +=ctreplacevalue;
        }
        return ciphertext;
    }
 
    public static String decrypt(String ciphertext, int shifts)
    {
    	// Converting into lowercase completely    	
        ciphertext = ciphertext.toLowerCase();
        
        String plaintext = "";
        for (int i = 0; i < ciphertext.length(); i++)
        {
            int ctvalue = ALPHABET.indexOf(ciphertext.charAt(i));
            int ptvalue = (ctvalue - shifts) % 26;
            if (ptvalue < 0)
            {
            	ptvalue = ALPHABET.length() + ptvalue;
            }
            char ptreplacevalue = ALPHABET.charAt(ptvalue);
            plaintext += ptreplacevalue;
        }
        return plaintext;
    }
 
    public static void main(String[] args)
    {
        Scanner s = new Scanner(System.in);
        System.out.println("Enter the plain text for encryption: ");
        String text = new String();
        text = s.next();
        System.out.println(" Cipher-Text is: "+encrypt(text, 5));
        System.out.println(" Plain-Text is: "+ decrypt(encrypt(text, 5), 5));
        s.close();
    }
}
