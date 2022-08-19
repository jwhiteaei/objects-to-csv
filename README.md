This is a fork! The toDisk method of the original was removed for browser use in React
https://github.com/anton-bot/objects-to-csv

# Convert array of objects into a CSV file #

Converts an array of JavaScript objects into the CSV format. You can
save the CSV to file or return it as a string.

The keys in the first object of the array will be used as column names.

Any special characters in the values (such as commas) will be properly escaped.

## Usage ##

```js
const ObjectsToCsv = require('objects-to-csv');

// Sample data - two columns, three rows:
const data = [
  {code: 'CA', name: 'California'},
  {code: 'TX', name: 'Texas'},
  {code: 'NY', name: 'New York'},
];

// If you use "await", code must be inside an asynchronous function:
(async () => {
  const csv = new ObjectsToCsv(data);

  // Save to file: (This only works with the original objects-to-csv, removed here for browser use in React)
  // await csv.toDisk('./test.csv');

  // Return the CSV file as string:
  console.log(await csv.toString());
})();
```

## Methods ##

There is one method, `toString()`.

### async toString(header = true, allColumns = false) ###

Returns the CSV file as a string.

Two optional parameters are available:

- `header` controls whether the column names will be
returned as the first row of the file. Default is `true`. Set it to `false` to
get only the data rows, without the column names.
- `allColumns` controls whether to check every item for potential keys to process,
rather than only the first item; this will sort the columns alphabetically by key name.
Default is `false`. Set it to `true` to process keys that may not be present
in the first object of the array.

```js
const ObjectsToCsv = require('objects-to-csv');
const sampleData = [{ id: 1, text: 'this is a test' }];

async function printCsv(data) {
  console.log(
    await new ObjectsToCsv(data).toString()
  );
}

printCsv(sampleData);
```

## Requirements ##

Use Node.js version 8 or above.
