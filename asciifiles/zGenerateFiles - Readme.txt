installed by : npm i asciidoctor
add this to path F:\WEB_PROJECTS\angular2\myDemo\angularDemo\

run java file :
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.ArrayList;
import java.util.List;

/**
 *
 * @author yaniv
 */
public class TransformFiles {
    
    public static void main( String args[] ) {

        System.out.println(args[0]);
            for (String line : convertFile(args[0]))
                doCmd(line);
    }  
    
    public static List<String> convertFile(String fileName) {
        List<String> lines = new ArrayList<>();
        try {
            lines = Files.readAllLines(Paths.get(fileName));
        } catch (IOException e) {
            System.err.println("Error reading file: " + e.getMessage());
        }
        return lines;
    } 
    
    public static Process doCmd(String program) {
         try {
             
            ProcessBuilder builder = new ProcessBuilder("cmd.exe", "/c", program);
            builder.redirectErrorStream(true);
            return builder.start();             
         }catch (Exception err) {
             err.printStackTrace();
         }
         return null;
    }    
    
}


