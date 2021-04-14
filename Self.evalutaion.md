# What work did you get?
### Task
              1.Create a evaluation sheet for self and others.
              2.Put the formula of average in average column. 
              3.If average column Value is equal to or less than then row colure should be appear red.
# How to write formula ?

#### SUM(COUNTIF(C4:J4,"excellent")*5,COUNTIF(C4:J4,"Very good")*4,COUNTIF(C4:J4,"Good")*3,COUNTIF(C4:J4,"Satisfactory")*2,COUNTIF(C4:J4,"Fair")*1, COUNTIF(C4:J4,"Poor")*0)/COUNTA(C4:J4)**

# How does the formulae work?

### Excel AVERAGE Function

**Summary**
The Excel AVERAGE function calculates the average (arithmetic mean) of supplied numbers. AVERAGE can handle up to 255 individual arguments, which can include numbers, cell references, ranges, arrays, and constants.
      
      1.Get the average of a group of numbers
      2.Syntax = SUM(COUNTIF(range,"string1")*number1,COUNTIF(range,"string2")*number2)/COUNTA(range)
      3.The AVERAGE function calculates the average of string. To calculate the average, Excel sums all string and divides by the count of numeric values. This behavior can be replicated with the SUM and COUNT functions.

##### Notes 📝:

:black_circle: **AVERAGE automatically ignores empty cells and cells with text values(if condition not difine).

:black_circle: **AVERAGE includes zero values. Use AVERAGEIF or AVERAGEIFS to ignore zero values.

:black_circle: **Arguments can be supplied as constants, ranges, named ranges, or cell references.

:black_circle: **AVERAGE can handle up to 255 total arguments.

