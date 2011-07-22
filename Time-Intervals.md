> [[API Reference]] ▸ [[Time]]

**Time intervals** are irregular! For example, there are 60 seconds in a minute, but 24 hours in a day. Even more confusing, some days have 23 or 25 hours due to [daylight saving time](http://en.wikipedia.org/wiki/Daylight_saving_time), and the standard [Gregorian calendar](http://en.wikipedia.org/wiki/Gregorian_calendar) uses months of differing lengths. And then there are leap years and leap seconds!

To simplify manipulation of and iteration over time intervals, D3 provides a handful of time utilities in addition to the time [scale](Time-Scales) and [format](Time-Formatting). The utilities support both local time and UTC time. Local time is determined by the browser's JavaScript runtime; arbitrary time zone support would be nice, but requires access to the Olson zoneinfo files.

<a name="day" href="#day">#</a> d3.time.<b>day</b>(<i>date</i>)<br>
<a name="day_utc" href="#day_utc">#</a> d3.time.day.<b>utc</b>(<i>date</i>)

Returns the latest day boundary (midnight) before or equal to *date*.

<a name="days" href="#days">#</a> d3.time.<b>days</b>(<i>start</i>, <i>stop</i>)<br>
<a name="days_utc" href="#days_utc">#</a> d3.time.days.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the day boundaries (midnight) after or equal to *start* and before *stop*. 

<a name="hour" href="#hour">#</a> d3.time.<b>hour</b>(<i>date</i>)<br>
<a name="hour_utc" href="#hour_utc">#</a> d3.time.hour.<b>utc</b>(<i>date</i>)

Returns the latest hour boundary (e.g., 01 AM) before or equal to *date*.

<a name="hours" href="#hours">#</a> d3.time.<b>hours</b>(<i>start</i>, <i>stop</i>)<br>
<a name="hours_utc" href="#hours_utc">#</a> d3.time.hours.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the hour boundaries (e.g., 01 AM) after or equal to *start* and before *stop*. 

<a name="minute" href="#minute">#</a> d3.time.<b>minute</b>(<i>date</i>)<br>
<a name="minute_utc" href="#minute_utc">#</a> d3.time.minute.<b>utc</b>(<i>date</i>)

Returns the latest minute boundary (e.g., 01:23 AM) before or equal to *date*.

<a name="minutes" href="#minutes">#</a> d3.time.<b>minutes</b>(<i>start</i>, <i>stop</i>)<br>
<a name="minutes_utc" href="#minutes_utc">#</a> d3.time.minutes.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the minute boundaries (e.g., 01:23 AM) after or equal to *start* and before *stop*. 

<a name="month" href="#month">#</a> d3.time.<b>month</b>(<i>date</i>)<br>
<a name="month_utc" href="#month_utc">#</a> d3.time.month.<b>utc</b>(<i>date</i>)

Returns the latest month boundary (e.g., January 01) before or equal to *date*.

<a name="months" href="#months">#</a> d3.time.<b>months</b>(<i>start</i>, <i>stop</i>)<br>
<a name="months_utc" href="#months_utc">#</a> d3.time.months.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the month boundaries (e.g., January 01) after or equal to *start* and before *stop*. 

<a name="second" href="#second">#</a> d3.time.<b>second</b>(<i>date</i>)<br>
<a name="second_utc" href="#second_utc">#</a> d3.time.second.<b>utc</b>(<i>date</i>)

Returns the latest second boundary (e.g., 01:23:45 AM) before or equal to *date*.

<a name="seconds" href="#seconds">#</a> d3.time.<b>seconds</b>(<i>start</i>, <i>stop</i>)<br>
<a name="seconds_utc" href="#seconds_utc">#</a> d3.time.seconds.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the second boundaries (e.g., 01:23:45 AM) after or equal to *start* and before *stop*. 

<a name="week" href="#week">#</a> d3.time.<b>week</b>(<i>date</i>)<br>
<a name="week_utc" href="#week_utc">#</a> d3.time.week.<b>utc</b>(<i>date</i>)

Returns the latest week boundary (midnight Sunday) before or equal to *date*.

<a name="weeks" href="#weeks">#</a> d3.time.<b>weeks</b>(<i>start</i>, <i>stop</i>)<br>
<a name="weeks_utc" href="#weeks_utc">#</a> d3.time.weeks.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the week boundaries (midnight Sunday) after or equal to *start* and before *stop*. 

<a name="year" href="#year">#</a> d3.time.<b>year</b>(<i>date</i>)<br>
<a name="year_utc" href="#year_utc">#</a> d3.time.year.<b>utc</b>(<i>date</i>)

Returns the latest year boundary (midnight January 1st) before or equal to *date*.

<a name="years" href="#years">#</a> d3.time.<b>years</b>(<i>start</i>, <i>stop</i>)<br>
<a name="years_utc" href="#years_utc">#</a> d3.time.years.<b>utc</b>(<i>start</i>, <i>stop</i>)

Returns the year boundaries (midnight January 1st) after or equal to *start* and before *stop*. 