<center><h2>YAML (Yet Another Markup Language)</h2></center>
• often used configuration format.
• provides data in human-readable format.
• used for object serializable

<h3>File initialization</h3>
It starts with three dashes(-), indicates the start of the file.
---

<h3>Data Types and Representation</h3>
- Data is represented in key-value pairs.
- key is always a string and the value is a scalar, can be of any data type.
- Supports four Data types:
1. String: declared with singel quotes(’) or double quotes(”) or no quotes.
2. boolean: true or false
3. floating-point number: eg. 3.1243
4. array: each item is denoted by an indentation of two spaces.
5. dictionary: collection of different data types.
"myDict": {
  "item1": "string value",
  "item2": false,
  "item3": [
    "arr-item1": item1,
    "arr-item2": item2
  ]
}
whitespace are used for formatting and it forbids tabs
newline indicate next line i.e the end of a field.

<h3>Comments</h3>
Represented by a # symbol.
They take up the whole line or placed at the end of the fields
