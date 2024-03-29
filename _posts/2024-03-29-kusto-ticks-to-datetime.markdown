---
layout: post
title:  "Kusto Ticks to datetime"
date:   2024-03-23 23:00:08 -0500
categories: kusto
---

Sometimes, timestamp for a kusto ([ADX](https://learn.microsoft.com/en-us/azure/data-explorer/)) log gets emitted in C# ticks format. Here is a small kusto function to convert ticks into Kusto datetime:

### Example

```
let convertTicksToDateTime = (ticksVal:long)
{
    let st_datetime = make_datetime(1,1,1);
    datetime_add('millisecond', ticksVal / 10000, st_datetime)
};
print(convertTicksToDateTime(638473111058656497))
```

### Result
```
print_0
2024-03-29T12:11:45.8649984Z
```