Sed = Stream Editor
	
	$sed options [address]commands file(s)
	* sed 's/text1/text2/' data.txt
	* if file is not provided then sed that it's input from standard input
	* reads one line of data and process it
	* writes the output to standard output.
	* this process continue till the last line.
	* by default it doesn't change content of file. to make the change in file use -i option.
		sed -i 's/text1/text2/' data.txt
	
# Substitute Text
	sed 's/searchPattern/replacementText/flags' file
	* sed 's/Delhi/Ghaziabad/' city.txt   //this will replace only 1st occurrence of pattern 
	* sed 's/Delhi/Ghaziabad/3' city.txt   //this will replace only 3rd occurrence of pattern
	* sed 's/Delhi/Ghaziabad/g' city.txt   //this will replace all occurrence in each line
	* sed 's/Delhi/Ghaziabad/p' city.txt   //print the line in which replacement will occur
	* sed 's/Delhi/Ghaziabad/w file' city.txt   //save the modified line into file
	* sed 's/Delhi//g' city.txt   //delete the search pattern

# Addressing
	Line Addressing
		* sed '4s/Delhi/Ghaziabad/' city.txt   //Apply to 4th line
		* sed '3,8s/Delhi/Ghaziabad/' city.txt   //Apply to 3rd to 4th  line
		* sed '5,$s/Delhi/Ghaziabad/' city.txt   //Apply to 5th to end  line 
		* sed '$s/Delhi/Ghaziabad/' city.txt   //Apply to only end line 
		
	Context Addressing
		