# takeaways
- no noticable difference in transporting between 100 vs 1000 rows in excel or csv
- given same data excel files are smaller
  - excel also support multiple sheets (csv does not)
- excel file grows in size in relation to number of sheets
- Sending JSON:
  - given same data, sending json requires less bandwidth
  - sending json can eliminate unwanted sheets (sheets that are not the first sheet).  
    - but will eliminate original file (aka other sheets)
  - sending json requires frontend processing and xlsx library dependency
- Sending Original File:
  - given same data, requires more bandwidth than JSON
  - preserves original file and enables storage/retrieval
  - requires backend processing 

  

# generation
- used script to generate csvs and excels with 100 and 1000 data points, and to generate excel file with 2 sheets


# testing
- files/json POST to https://files.io
- inspect resource size
- send json over the network:
  - use xlsx dependency to parse the excel file
  - was only sending the first sheet's data

# comparison

|                               | Resource (Bytes) |
| -----------                   | ----------- |
| 100 csv file                  | 955       |
| 100 csv json                  | 64        |
| 100 xlsx file (1 sheet)       | 229       |
| 100 xlsx json (1 sheet)       | 64        |
| 1000 csv file                 | 955       |
| 1000 csv json                 | 64        |
| 1000 xlsx file (1 sheet)      | 229       |
| 1000 xlsx json (1 sheet)      | 156       |
| 1000 xlsx file (2 sheet)      | 955       |
| 1000 xlsx json (2 sheet)      | 64        |
| 100 xlsx file (2 sheet)       | 955       |
| 100 xlsx json (2 sheet)       | 64        |
