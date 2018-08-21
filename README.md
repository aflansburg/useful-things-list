# Useful things I use
List of utilities, such as npm packages, that I enjoy using

## Node.js
---

### CSV Reading
* [Papa Parse](https://www.papaparse.com/) -> [Repo Here](https://github.com/mholt/PapaParse)

> #### Using Papa Parse
```
const fs = require('fs');
const Papa = require('papaparse');
const file = './data/input/all_superseded.csv';

// config for papaparse
const config = {
    header: true,
    encoding: 'utf8',
    delimiter: ',',
}

// read the csv file
const csvData = fs.readFileSync(file, 'utf8');

// parse the file object and filter on a specific prop
let data = Papa.parse(csvData, config).data.filter(d=>d.MPN !== '')
```
### CSV Writing
* [csv-write-stream](https://github.com/maxogden/csv-write-stream)

### XML Parsing

* [node-xml2js](https://github.com/Leonidas-from-XIV/node-xml2js)
* [Simple XML2JSON Parser](https://www.npmjs.com/package/xml2json)

## XHR
* [request/request-promise-native](https://github.com/request/request-promise-native)
Which requires:
    * [request/request](https://github.com/request/request)

### Throttling
* [bottleneck](https://github.com/SGrondin/bottleneck#readme)

### Querying SQL DB
* [node-mssql](https://github.com/tediousjs/node-mssql)

### SOAP client
* [node-soap](https://github.com/vpulim/node-soap)

### Dealing with Time
* [moment.js](https://momentjs.com/)

### Parsing Command Line Arguments (node.js)
* [argparse](https://www.npmjs.com/package/argparse)

---
Python Examples
---
### Reading CSV

```
import csv
with open('eggs.csv', newline='') as csvfile:
   spamreader = csv.reader(csvfile, delimiter=' ', quotechar='|')
   for row in spamreader:
      print(', '.join(row))
```

### Writing CSV
```
import csv
with open('eggs.csv', 'w', newline='') as csvfile:
   spamwriter = csv.writer(csvfile, delimiter=' ',
                           quotechar='|', quoting=csv.QUOTE_MINIMAL)
   spamwriter.writerow(['Spam'] * 5 + ['Baked Beans'])
   spamwriter.writerow(['Spam', 'Lovely Spam', 'Wonderful Spam'])
```

### Reading Dictionaries
```
import csv
with open('names.csv', newline='') as csvfile:
   reader = csv.DictReader(csvfile)
   for row in reader:
      print(row['first_name'], row['last_name'])
```

### Writing Dictionaries
```
import csv

with open('names.csv', 'w', newline='') as csvfile:
   fieldnames = ['first_name', 'last_name']
   writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

   writer.writeheader()
   writer.writerow({'first_name': 'Baked', 'last_name': 'Beans'})
   writer.writerow({'first_name': 'Lovely', 'last_name': 'Spam'})
   writer.writerow({'first_name': 'Wonderful', 'last_name': 'Spam'})
```

### Reading CSV + Writing to file + Concatenating values from a single column csv
```
import csv

file = open("C:\\Users\\aflansburg\\Downloads\\itemtypeString.txt", "w+")
typeString = ''
with open('C:\\Users\\aflansburg\\Downloads\\itemtype.csv') as csvfile:
    reader = csv.reader(csvfile, delimiter=',')
    for index, r in enumerate(reader):
        if len(typeString) > 0 and index < len(typeString):
            typeString += ',' + r[0]
        else:
            typeString += r[0]

file.write(typeString)
```
