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
