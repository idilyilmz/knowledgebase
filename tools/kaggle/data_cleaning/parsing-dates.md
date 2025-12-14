# (3) Parsing Dates

https://www.kaggle.com/code/alexisbcook/parsing-dates

## 1. Get our environment set up
- import common libraries
    - `pandas`, `numpy` for data handling
    - `seaborn` for visualization
    - `datetime` fpr working with date/time objects
- load a dataset containing landslide events
- set a random seed for reproducibility

## 2. Check the data type of our date column
- inspect the dataset using `head()` to see how dates are stored
- although the date values *look* like dates, pandas stores them as **object** (string) dtype
- pandas cannot treat dates as dates unless they are explicitly converted to a datetime type
- use `.dtype` to confirm column data types

## 3. Convert our data columns to datetime
- convert string dates to datetime objects using `pd.to_datetime()`
- this process is called **parsing data**
- specify the date format using **stfttime directives**, like
    - `%m` → month
    - `%d` → day
    - `%y` → two-digit year
    - `%Y` → four-digit year
- example format used: `%m/%d/%y`
- after parsing, the column dtype becomes `datetime64`

### a. Handling multiple date formats:
- use `infer_datetime_format=True` if formats vary.
- downsides: 
    - slower performance
    - may misinterpret ambigious formats
- prefer specifying the format when possible

## 4. Select the day of the month
- once parsed, across date components using the `.dt` accessor
- example: extract the day of the month with `.dt.day`
- this only works on columns with datetime dtype.
- attempting this on an object column raises an error

## 5. Plot the day of the month to check the date parsing
- plot a histogram of the extracted day values
- expected results:
    - values between **1 and 31**
    - roughly even distribution
    - fewer values on day 31 (not all month have 31 days)
- visualization helps catch error such as swapped month/day values

## 6. Key takeaways
- dates must be **parsed** before pandas can work with them properly
- always verify parsed dates using logic or visualization
- correct date parsing enables powerful time-based analysis
