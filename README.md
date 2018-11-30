# CSVCount
PHP script mimicking basic functionality of the coreutils `wc -l`, for CSV files. I have done this for fun, but it's worth noting `fgetcsv` is really REALLY slow. If you need to count the number of records of big CSV files, go with this Python oneliner:

```
cat * | python -c "import csv; import sys; print(sum(1 for i in csv.reader(sys.stdin)))"
```

## Installation
Clone the repository, copy the script file to your path `(/home/<user>/bin, /home/<user>/.local/bin, /usr/local/bin, ...)` and assign execute permission:
```
git clone https://github.com/dhulke/CSVCount.git
mkdir /home/<user>/bin
cd CSVCount
cp csvcount /home/<user>/bin/csvcount
```

## Usage
Use it as you would `wc -l`, but for CSV files:

```
echo 'column1, column2, column3
11, 12, 13
21,"multiline 22 
value", 23
31, 32, 33' | csvcount

cat *.csv | csvcount

csvcount *.csv
```

## Todo
* Explore other ways of parsing CSV other than using the slow `fgetcsv`.
* Implement command line options to set delimiter, enclosure, escape, encoding and others
* Composer