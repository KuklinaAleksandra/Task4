# Task4
Создать проект, позволяющий из одного текстового  файла, содержащего несколько строк (тип String) заранее  подготовленного текста на русском языке (обратитесь к классике),  построчно переписать в другой текстовый файл слова, отвечающие  условию.

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;


public class Task2 {

	public static void main(String[] args) throws IOException{ 
		BufferedReader br = null;
		BufferedWriter out=null;
		try {
			br = new BufferedReader( new FileReader("C:\\Test\\task2_input.txt"), 1024);
			out = new BufferedWriter( new FileWriter( " C:\\Test\\task2_output.txt" ));
			int lineCount = 0;
			String s;
			while ((s = br.readLine()) != null) {
				s = s.replace('.', ' ').replace(',', ' ').replace('—', ' ').trim();
				String[] allWords = s.split("\s+");
				out.write("Строка номер " + lineCount++ + ", количество слов: " + allWords.length);
				out.newLine();
				if (allWords.length > 0) {					
					for (int i = 0; i < allWords.length; i++) {
						if (!allWords[i].isBlank() && !allWords[i].isEmpty()) {
							if(allWords[0].charAt(0) == allWords[i].charAt(0)) {
								out.write(allWords[i] + " ");
							}	
						}
					}	
					out.newLine();
				}
			}
		} catch (IOException e) { System.out.println("Ошибка !!!!!!!!");
		}
		finally{
			br.close();
			out.flush();
			out.close();
		}
}}
