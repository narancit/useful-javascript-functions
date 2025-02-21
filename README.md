# Useful Javascript Functions

### Function that converts 24 hour format to 12 hour format

```
function convertTimeTo12HrFormat(time) {
    // Check correct time format and split into components
    time = time
        .toString()
        .match(/^([01]\d|2[0-3])(:)([0-5]\d)(:[0-5]\d)?$/) || [time];

    if (time.length > 1) {
        // If time format correct
        time = time.slice(1); // Remove full string match value
        time[5] = +time[0] < 12 ? ' AM' : ' PM'; // Set AM/PM
        time[0] = +time[0] % 12 || 12; // Adjust hours
    }
    return time.join(''); // return adjusted time or original string
}

/*
    Sample Outputs:
    18:00:00 => "6:00:00 PM"
    18:00 => "6:00 PM"
    00:00 => "12:00 AM"
    11:59:01 => "11:59:01 AM"
    12:00:00 => "12:00:00 PM"
    13:01:57 => "1:01:57 PM"
    24:00 => "24:00"
    sdfsdf => "sdfsdf"
    12:61:54 => "12:61:54"
*/
```

### This code adds a custom method called toProperCase to JavaScript's built-in String prototype. This method converts a string to "proper case" (also called "title case"), where the first letter of each word is capitalized and the remaining letters are lowercase.

```
String.prototype.toProperCase = function () {
    return this.replace(/\w\S*/g, function (txt) {
        return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
    });
};

let sentence = "hello world, this is a test!";
let properCaseSentence = sentence.toProperCase();
console.log(properCaseSentence);
// Sample Output: "Hello World, This Is A Test!"
```
