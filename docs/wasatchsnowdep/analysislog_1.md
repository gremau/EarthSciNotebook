**5/10/2011**

* Cleaned up the pm2.5 data using find/replace in vim
* Rebuilt the sampletracking data file from the spreadsheet, removing some bad data/samples
* Made worksheet for filtering samples
* Generated timeline graphs of all samples taken (all and by category), and those sent/to-be-sent to Kiowa

**5/9/2011**

* Created a sample log file for matlab (sampletracking_110505.txt).
* Downloaded hourly pm2.5 data provided by DAQ from [PCAPS page](http://pcaps.utah.edu).
  * This data is in separate files for each day, so I concatenated them into one file with a bash script (see below)
* Created a matlab script that reads sample log file and pm2.5 data and outputs a timeline of samples taken, and which have been run.

Bash code to concatenate the daily pm2.5 files (minus headers in each
file)

~~~{.bash}
# Run from directory containing all files
# Last 24 lines in each file contain the data (the top is all header stuff)
for i in *.txt; do tail -24 "$i" >> newfile.txt; done
~~~
