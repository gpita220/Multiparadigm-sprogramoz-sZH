# Multiparadigmás-programozozás-ZH-Galvács István-JHPIPM
https://github.com/Zsolt-Toth-EKU/20121220-gpita220
package hu.uni.ekcu.java.service;
import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;

public class NGramm {
    List<String> list = new ArrayList<String>();
    public String read(String file) {
        File f = new File(file);
        String st = "";
        try {
            BufferedReader br = new BufferedReader(new FileReader(f));
            while((st = br.readLine()) != null) {

            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return st;
    }
    public List<String> ngramm(String file, int n){
        String text = read(file);
        String firstThreeChars = "";
        String[] words = text.split(" ");
        for (int i = 0; i < words.length; i++) {
            if(words[i].length() > n) {
                firstThreeChars = words[i].substring(0, n);
                list.add(firstThreeChars);
            }
        }
        return list;
    }
    public HashMap<String, Integer> statistics() {
        HashMap<String, Integer> map = new HashMap<>();
        for (int i = 0; i < list.size(); i++) {
            if(!(map.containsKey(list.get(i).toLowerCase()))) {
                map.put(list.get(i).toLowerCase(), 1);
            }
            else {
                map.put(list.get(i).toLowerCase(), map.get(list.get(i).toLowerCase()) + 1);
            }
        }
        return map;
    }
}
