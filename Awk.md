It name based on initial letter of creater = Aho weinberger and Kerninghan

# $awk option 'selection_criteria {command}' file(s)
	
	Reads one line at a time from input stream and applies the commands on it.
	Does not make any changes to input file.
	
	* awk 'London/{print}' data.txt    //print those line have pattern
	* awk 'London/' data.txt    	  //print those line match with pattern, because print is default command
	* awk '{print}' data.txt    	  //print all the lines, if not selection_criteria available
	
# Fields and Records
	$1 First field of the line 			NF - Total number of fields in an input
	$2 2nd field of the line 
	$3 3rd field of the line 
	---------------------
	----------------------
	$NF Last field of the line
	$0 Entire line
	
	awk '{print}' data.txt   == awk '{print $0}' data.txt   //print whole line
	awk '{print $1,$4}' data.txt							//print 1st and 4th field
	awk '{print $1,$NF}' data.txt							//print 1st and last field
	awk '{print $1,"Hello",$NF}' data.txt	== Delhi Hello Bombay		//print 1st and last field
	
example 
	ls -ltra  | awk '{print $1}' 
	total
	-rw-r--r--
	drwxrwxr-x


# Specify field delimiter
	-F allow to put single character for delimiter
	awk -F'|' '{print $2}' data.txt  // | delimiter

# Multiple Command
	awk '{ $3=$3+400; print $0}'  data.txt

# Command from file
	file.awk 
	{
	$2=$2+300;
	$3=$3-50;
	print $1,":",$3;
	}
	
	file.awk 
	/London/{print $1,":",$3;}
	/Berlin/{print $1,":",$3;}
	
	awk -f file.awk data.txt
	
# Variables
	FILENAME 
	NR    Line no
	FS 	  input line separator
   	awk '{print NR,$0}'  data.txt  // print all line with line no
	awk 'NR==2,NR==5{print NR,$0}'  data.txt  // Line no 2 to line 5
	awk 'NR==2 || NR==5{print NR,$0}'  data.txt  // Line no 2 or 5
	awk 'NR==2,/Delhi/{print NR,$0}'  data.txt  // Line no 2 to 1st occurrence of Delhi
	awk 'NR!=1{print NR,$0}'  data.txt  // all line not 1st line
	awk '$3>500{print NR,$0}'  data.txt  // all line not 1st line
	awk 'Total=$1+$2+3{print NR,$0,Total}'  data.txt  // all line not 1st line
	awk 'Total=$1+$2+3{print("%s %d %.2f \n",$0,Total,Total/300*100}'  data.txt  // all line not 1st line
	
