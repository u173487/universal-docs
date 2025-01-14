---
description: Displays a numeric statistic on a page.
---

# Statistic

Numeric statistics can return data from scripts and APIs and display values with some amount of formatting options.&#x20;

## Display a statistic from an API

APIs should return a single value to display as a statistic. An example API could look something like this.&#x20;

```
Get-Random -Min 100 -Max 1000
```

You can then select the API under the data source tab.&#x20;

![](<../../.gitbook/assets/image (266).png>)

Each time the page is loaded, the API is called and the random value is shown.&#x20;

![](<../../.gitbook/assets/image (268).png>)

## Display a statistic from a Script

Statistics shown from scripts will display the value return by the last job run for the script. Loading the page will not run the script again.&#x20;

We will use this script as an example.

```
Get-Random -Min 100 -Max 1000
```

Select the script on the data source tab.&#x20;

![](<../../.gitbook/assets/image (269).png>)

The statistic will be shown on the page based on the output of the script. You'll notice that refreshing the page does not change the value of the statistic unless the job is run again.&#x20;

![](<../../.gitbook/assets/image (270).png>)

## Customizing the Statistic

You can customize features such as the prefix, suffix, precision and whether to auto-reload the statistic on an interval.&#x20;

![](<../../.gitbook/assets/image (271).png>)

![](<../../.gitbook/assets/image (272).png>)

## Properties

| Property             | Description                                                | Available Since |
| -------------------- | ---------------------------------------------------------- | --------------- |
| ID                   | The ID of this component                                   | 2.2.0           |
| Title                | The text to display within the statistic.                  | 2.2.0           |
| Data Source          | The script or API to call to return the statistic's value. | 2.2.0           |
| Prefix               | The string to display before the value.                    | 2.2.0           |
| Suffix               | The string to display after the value.                     | 2.2.0           |
| Auto Reload          | Whether to auto-reload the statistic on an interval.       | 2.2.0           |
| Auto Reload Interval | The number of seconds between auto-reloads.                | 2.2.0           |
| Precision            | The number of decimal places to display in the value.      | 2.2.0           |

