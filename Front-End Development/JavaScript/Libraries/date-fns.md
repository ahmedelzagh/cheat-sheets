# date-fns in JS

`date-fns` is a popular JavaScript library for working with dates and times. It provides a lightweight (2.8KB minified and gzipped) and modern API for manipulating and formatting dates and times. `date-fns` is designed to be a more efficient and intuitive alternative to the built-in `Date` object in JavaScript.

With `date-fns`, you can perform various operations on dates and times, such as:
- Adding or subtracting time
- Formatting dates
- Comparing dates
- Calculating the difference between dates

The library provides over 130 functions for working with dates, and all functions are pure, meaning that they don't modify the original values passed in and return new values instead.

`date-fns` is widely used in modern web applications and is considered a go-to library for date and time manipulation in JavaScript. Its small size and comprehensive API make it a popular choice for developers who need a reliable and efficient solution for working with dates and times in their projects.

![[data-fns.png]]

## Popular Functions in `date-fns`

### format
Formats a date into a string representation according to a specified format.
```js
import { format } from 'date-fns';

const date = new Date(2022, 0, 1, 0, 0, 0, 0);
const formatted = format(date, 'MM/dd/yyyy');
console.log(formatted); // '01/01/2022'
```

### addDays
Adds a specified number of days to a date.
```js
import { addDays } from 'date-fns';

const date = new Date(2022, 0, 1, 0, 0, 0, 0);
const newDate = addDays(date, 10);
console.log(newDate); // 2022-01-11T00:00:00.000Z
```

### subtract
Subtracts two dates and returns the difference between them in a specified unit of time.
```js
import { subtract } from 'date-fns';

const date1 = new Date(2022, 0, 1, 0, 0, 0, 0);
const date2 = new Date(2022, 0, 5, 0, 0, 0, 0);
const difference = subtract(date2, date1);
console.log(difference); // 4 * 24 * 60 * 60 * 1000
```

### isBefore
Checks if a date is before another date.
```js
import { isBefore } from 'date-fns';

const date1 = new Date(2022, 0, 1, 0, 0, 0, 0);
const date2 = new Date(2022, 0, 5, 0, 0, 0, 0);
const isBefore = isBefore(date1, date2);
console.log(isBefore); // true
```

There are many more functions available in `date-fns`, these are just a few examples.