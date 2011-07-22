> [[API Reference]] ▸ [[Time]]

D3's **time scale** is an extension of [d3.scale.linear](Quantitative-Scales#linear) that uses JavaScript [Date](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date) objects as the domain representation. Thus, unlike the normal linear scale, domain values are coerced to dates rather than numbers; similarly, the [invert](#invert) function returns a date. Most conveniently, the time scale also provides suitable [ticks](#ticks) based on [time intervals](Time-Intervals), taking the pain out of generating axes for nearly any time-based domain.

A scale object, such as that returned by [d3.time.scale](#scale), is both an object and a function. That is: you can call the scale like any other function, and the scale has additional methods that change its behavior. Like other classes in D3, scales follow the method chaining pattern where setter methods return the scale itself, allowing multiple setters to be invoked in a concise statement.

<a name="scale" href="#scale">#</a> d3.time.<b>scale</b>()

Constructs a new time scale with the default domain and range; the ticks and tick format are configured for local time.

<a name="utc" href="#utc">#</a> d3.time.scale.<b>utc</b>()

Constructs a new time scale with the default domain and range; the ticks and tick format are configured for UTC time.

<a name="_scale" href="#_scale">#</a> <b>scale</b>(<i>x</i>)

Given a date *x* in the input domain, returns the corresponding value in the output range.

<a name="invert" href="#invert">#</a> scale.<b>invert</b>(<i>y</i>)

Returns the date in the input domain *x* for the corresponding value in the output range *y*. This represents the inverse mapping from range to domain. For a valid value *y* in the output range, scale(scale.invert(*y*)) equals *y*; similarly, for a valid date *x* in the input domain, scale.invert(scale(*x*)) equals *x*. The invert operator is particularly useful for interaction, say to determine the date in the input domain that corresponds to the pixel location under the mouse.

<a name="domain" href="#domain">#</a> scale.<b>domain</b>([<i>dates</i>])

If *dates* is specified, sets the scale's input domain to the specified array of dates. The array must contain two or more dates. If the elements in the given array are not dates, they will be coerced to dates; this coercion happens similarly when the scale is called. If *dates* is not specified, returns the scale's current input domain. Although time scales typically have just two dates in their domain, you can specify more than two dates for a *polylinear* scale. In this case, there must be an equivalent number of values in the output range.

<a name="range" href="#range">#</a> scale.<b>range</b>([<i>values</i>])

If *values* is specified, sets the scale's output range to the specified array of values. The array must contain two or more values, to match the cardinality of the input domain. The elements in the given array need not be numbers; any value that is supported by the underlying [interpolator](#interpolate) will work. However, numeric ranges are required for the invert operator. If *values* is not specified, returns the scale's current output range.

<a name="rangeRound" href="#rangeRound">#</a> scale.<b>rangeRound</b>([<i>values</i>])

Sets the scale's output range to the specified array of values, while also setting the scale's interpolator to [[d3.interpolateRound|Transitions#d3_interpolateRound]]. This is a convenience routine for when the values output by the scale should be exact integers, such as to avoid antialiasing artifacts. It is also possible to round the output values manually after the scale is applied.

<a name="interpolate" href="#interpolate">#</a> scale.<b>interpolate</b>([<i>factory</i>])

If *factory* is specified, sets the scale's output interpolator using the specified *factory*. The interpolator factory defaults to [[d3.interpolate|Transitions#d3_interpolate]], and is used to map the normalized domain parameter *t* in [0,1] to the corresponding value in the output range. The interpolator factory will be used to construct interpolators for each adjacent pair of values from the output range. If *factory* is not specified, returns the scale's interpolator factory.

<a name="clamp" href="#clamp">#</a> scale.<b>clamp</b>([<i>boolean</i>])

If *boolean* is specified, enables or disables clamping accordingly. By default, clamping is disabled, such that if a value outside the input domain is passed to the scale, the scale may return a value outside the output range through linear extrapolation. For example, with the default domain and range of [0,1], an input value of 2 will return an output value of 2. If clamping is enabled, the normalized domain parameter *t* is clamped to the range [0,1], such that the return value of the scale is always within the scale's output range. If *boolean* is not specified, returns whether or not the scale currently clamps values to within the output range.

<a name="ticks" href="#ticks">#</a> scale.<b>ticks</b>(<i>count</i>)

Returns approximately *count* representative dates from the scale's input domain. The returned tick dates are uniformly spaced (modulo irregular time intervals, such as months and leap years), have human-readable values (such as midnights), and are guaranteed to be within the extent of the input domain. Ticks are often used to display reference lines, or tick marks, in conjunction with the visualized data. The specified *count* is only a hint; the scale may return more or fewer values depending on the input domain.

The following time intervals are considered:

* 1-, 5-, 15- and 30-[second](Time-Intervals#second).
* 1-, 5-, 15- and 30-[minute](Time-Intervals#minute).
* 1-, 3-, 6- and 12-[hour](Time-Intervals#hour).
* 1- and 2-[day](Time-Intervals#day).
* 1-[week](Time-Intervals#week).
* 1- and 3-[month](Time-Intervals#month).
* 1-[year](Time-Intervals#year).

This set of time intervals is somewhat arbitrary and additional values may be added in the future.

<a name="tickFormat" href="#tickFormat">#</a> scale.<b>tickFormat</b>(<i>count</i>)

Returns a [[time format|Time-Formatting]] function suitable for displaying a tick value. The specified *count* should have the same value as the count that is used to generate the tick values. You don't have to use the scale's built-in tick format, but it automatically computes the appropriate display based on the input date.

The following time formats are considered:

* %Y - for year boundaries, such as "2011".
* %B - for month boundaries, such as "February".
* %b %d - for week boundaries, such as "Feb 06".
* %a %d - for day boundaries, such as "Mon 07".
* %I %p - for hour boundaries, such as "01 AM".
* %I:%M - for minute boundaries, such as "01:23".
* :%S - for second boundaries, such as ":45".

By using multi-scale time formats, the default tick format provides both local and global context for each time interval. For example, by showing the sequence [11 PM, Mon 07, 01 AM], the tick formatter reveals information about hours, dates, and day simultaneously—rather than just the hours. If you'd prefer single-scale time formatting, you can always use your own [d3.time.format](Time-Formatting).