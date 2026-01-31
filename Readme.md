# Data Problems and Cleaning Procedures:

## Duplicates

- Sorted the data by order date, then counted the number of duplicates in the OrderID column (=IF(COUNTIF($A$2:2, A2)=1, "Original", "Duplicate").

- The criteria applied is that the oldest OrderID is the original, and subsequent similar OrderIDs are duplicates.

-Next, filtered the duplicate column and deleted all rows with duplicates.

## MISSING VALUES

- Missing values were handled using business-appropriate placeholders. City and Channel fields were replaced with “Unknown” where data was missing to avoid inaccurate assumptions while still retaining the sales records for analysis. Missing salesperson values were labeled as “Unassigned” to reflect incomplete attribution without removing valid transactions.

## Negative Unit Price

Negative UnitPrice values were treated as data entry errors rather than unit prices, as unit prices cannot be negative in standard sales records and no return indicator was present in the dataset. These values were corrected by calculating the price by assuming a 20% markup above the unit cost.

## DISCOUNT > 30%

-  A discount value greater than 30% was considered a data entry error; the discounts greater than 30% were flagged and capped at 30%.

## Required Date Fixed

- RequiredDate values earlier than OrderDate were flagged as invalid, as orders cannot be required before being placed. These records were corrected by imputing a RequiredDate equal to the OrderDate plus a standard processing period of five calendar days.
