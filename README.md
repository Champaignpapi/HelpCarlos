# HelpCarlospackage FinalExam;

import java.nio.file.*;
import java.io.*;
import java.nio.file.attribute.*;
import static java.nio.file.StandardOpenOption.*;
import java.nio.ByteBuffer;
import java.nio.channels.FileChannel;
import java.util.Scanner;


public class DisplaySavedCustomerList {
	
	public static void main(String[] args) {
		
		final String ID_FORMAT = "000";
		final String NAME_FORMATE = "            ";
		final int NAME_LENGTH = NAME_FORMATE.length();
		final String BALANCE_OWED_FORMAT = "0000.00";
		String delimiter = ",";
		String s = ID_FORMAT + delimiter + NAME_FORMATE + NAME_FORMATE + delimiter +
				BALANCE_OWED_FORMAT+ System.getProperty("line.separator");
		final int RECSIZE = s.length();
		
	//fn stands for file name.	
		Scanner fn = new Scanner(System.in);
		String fileName;
		System.out.println("Enter the name of the you would like to pull");
		fileName = fn.nextLine();
		fileName = "/Users/carloschampaign/eclipse-workspace1/school"
				+ fileName;
		Path file = Paths.get(fileName);
		
		byte records[] = s.getBytes();
		final String EMPTY_ACCT = "000";
		String[] array = new String[5];
		double balanceOwed;
			
		try {
			InputStream iStream = 
					new BufferedInputStream(Files.newInputStream(file));
            BufferedReader reader = 
            		new BufferedReader(new InputStreamReader(iStream));
            System.out.println("\nAll non-default records: \n");
            s = reader.readLine();
            
            while(s != null) {
            		array = s.split(delimiter);
            				
            			balanceOwed = Double.parseDouble(array[3]);
            			System.out.println("ID holder #" + array[0] + " " + array[1] +
            					array[2]	 + " $" + array[3] );
            		}
            		s = reader.readLine();
             reader.close();
           
		}
		catch(IOException e) {
			System.out.println("error " );
		}

	}

}
