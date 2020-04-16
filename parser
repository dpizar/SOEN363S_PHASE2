import java.io.BufferedReader;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;
 
public class Converter{
    static String line;    	//to read in each line
    static Stack stack;    	//to store each line of data
    static File outputFile;    //output file to be returned
    static File finalOutput;
    static BufferedReader br;  //used to read in bytes from file
    static FileWriter writer;  //used to write bytes to file
 
    @SuppressWarnings({ "unchecked", "rawtypes" })
        	public File convertFromTabToCSV(File inputFile) {
        outputFile = new File("convertedCsv.csv");
        
        try {
            stack = new Stack();
            br = new BufferedReader(new FileReader(inputFile));
            writer = (new FileWriter(outputFile));
            while ((line = br.readLine()) != null)
                stack.push(line.replace("\t", ","));
            while(!stack.isEmpty()){
                writer.write((String) stack.pop());
                if (!stack.empty())
                    writer.write("\n");
                }
 
        }
        catch (FileNotFoundException a) {
            System.out.println("Could not open file");
            a.printStackTrace();
        }
        catch(IOException b){
                System.out.println("IOException occured");
                b.printStackTrace();
        }
        catch(Exception c){
            c.printStackTrace();
        }
  	          finally {
                	try{
                    	br.close();
                    	writer.close();
                	}
                	catch(IOException d){
                        System.out.println("IOException, unable to close streams");
                    	d.printStackTrace();
                	}
            }
        
        return outputFile;
	}
    @SuppressWarnings({ "unchecked", "rawtypes" })
        	public static File convertFromCSVToTab(File inputFile) {
        outputFile = new File("C:\\Users\\Administrator.MTL254\\Downloads\\17100138-eng-1\\17100138_converted.csv");
        try {
            stack = new Stack();
           
            br = new BufferedReader(
                                                    	   new InputStreamReader(
                           	new FileInputStream(inputFile), "UTF8"));
            //br = new BufferedReader(new FileInputStream(inputFile));
            writer = (new FileWriter(outputFile));
            while ((line = br.readLine()) != null)
                          	
                stack.push(line.replace("è", "e").replace("é", "e").replace("ô","o").replace("Î", "I"));
            while(!stack.isEmpty()){
                writer.write((String) stack.pop());
                if (!stack.empty())
                    writer.write("\n");
            }
 
        }
        catch (FileNotFoundException a) {
            System.out.println("Could not open file");
            a.printStackTrace();
        }
        catch(IOException b){
            System.out.println("IOException occured");
            b.printStackTrace();
        }
        catch(Exception c){
            c.printStackTrace();
        }
        finally {
            try{
                br.close();
                writer.close();
            }
            catch(IOException d){
                System.out.println("IOException, unable to close streams");
                d.printStackTrace();
            }
        }
 	
        return outputFile;
	}
	
    public static void main(String[] args) {
                                	File inputFile = new File("C:\\Users\\Administrator.MTL254\\Downloads\\17100138-eng-1\\17100138.csv");
                                	convertFromCSVToTab(inputFile);
                                	/*inputFile = outputFile;
                                	
                                	convertFromCSVToTab(inputFile, "é", "e");*/
        	}

}
