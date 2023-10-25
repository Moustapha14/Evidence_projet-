---
sidebar_position: 5
title: Line Chart
hide_table_of_contents: false
---

![line](/img/exg-line-nt.svg)

```markdown
<LineChart 
    data={query_name}  
    x=column_x 
    y=column_y
/>
```

## Examples

### Line

![line](/img/exg-line-nt.svg)

```markdown
<LineChart 
    data={daily_complaints} 
    x=date 
    y=number_of_complaints 
    yAxisTitle="calls to Austin 311 per day"
/>
```

### Multi-Series Line

![multi-series-line](/img/exg-multi-series-line-nt.svg)

```markdown
<LineChart 
    data={daily_volume_yoy} 
    x=day_of_year 
    y=cum_vol 
    series=year 
    yAxisTitle="cumulative calls" 
    xAxisTitle="day of year"
/>
```

### Multi-Series Line with Steps

<img src='/img/exg-multi-series-step-line.png' width='576px'/>

```markdown
<LineChart
    data={simpler_bar}
    x=year
    y=value
    series=country
    step=true
/>
```

### Multiple y Columns

![multiple-y-line](/img/exg-multiple-y-line-nt.svg)

```markdown
<LineChart
data={fda_recalls}  
 x=year
y={["voluntary_recalls", "fda_recalls"]}
/>
```

Because x is the first column in the dataset and we want to plot all the remaining numerical columns in the table, we can simplify our code down to:

```markdown
<LineChart data={fda_recalls}/>
```

Evidence will automatically pick the first column as `x` and use all other numerical columns for `y`.

### Secondary y Axis

<img src="/img/multi-y-axes.png"  width='700px'/>

```markdown
<LineChart 
    data={orders_by_month} 
    x=month 
    y=sales_usd0k 
    y2=num_orders_num0
/>
```

### Value Labels

<img src="/img/line-labels.png"  width='700px'/>

```markdown
<LineChart 
    data={orders_by_month} 
    x=month
    y=sales
    yAxisTitle="Sales per Month"
    yFmt=eur0k
    labels=true
/>
```


### Custom Color Palette

<img src="/img/line-colorpalette.png"  width='700px'/>

```markdown
<LineChart 
  data={simpler_bar} 
  x=year 
  y=value 
  series=country
  colorPalette={
        [
        '#cf0d06',
        '#eb5752',
        '#e88a87',
        '#fcdad9',
        ]
    }
/>
```



## Options

### Data

<table>						 
<tr>	<th class='tleft'>Name</th>	<th class='tleft'>Description</th>	<th>Required?</th>	<th>Options</th>	<th>Default</th>	</tr>
<tr>	<td>data</td>	<td>Query name, wrapped in curly braces</td>	<td class='tcenter'>Yes</td>	<td class='tcenter'>query name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>x</td>	<td>Column to use for the x-axis of the chart</td>	<td class='tcenter'>Yes</td>	<td class='tcenter'>column name</td>	<td class='tcenter'>First column</td>	</tr>
<tr>	<td>y</td>	<td>Column(s) to use for the y-axis of the chart</td>	<td class='tcenter'>Yes</td>	<td class='tcenter'>column name | array of column names</td>	<td class='tcenter'>Any non-assigned numeric columns</td>	</tr>
<tr>	<td>y2</td>	<td>Column(s) to include on a secondary y-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>column name | array of column names</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>series</td>	<td>Column to use as the series (groups) in a multi-series chart</td>	<td class='tcenter'>-</td>	<td class='tcenter'>column name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>sort</td>	<td>Whether to apply default sort to your data. Default is x ascending for number and date x-axes, and y descending for category x-axes</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>handleMissing</td>	<td>Treatment of missing values in the dataset</td>	<td class='tcenter'>-</td>	<td class='tcenter'>gap | connect | zero</td>	<td class='tcenter'>gap</td>	</tr>
</table>

### Formatting & Styling

<table>						 
<tr>	<th class='tleft'>Name</th>	<th class='tleft'>Description</th>	<th>Required?</th>	<th>Options</th>	<th>Default</th>	</tr>
<tr>	<td>xFmt</td>	<td>Format to use for x column (<a href='/core-concepts/formatting'>see available formats</a>)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>Excel-style format | buil-in format name | custom format name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>yFmt</td>	<td>Format to use for y column(s) (<a href='/core-concepts/formatting'>see available formats</a>)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>Excel-style format | buil-in format name | custom format name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>y2Fmt</td>	<td>Format to use for y2 column(s) (<a href='/core-concepts/formatting'>see available formats</a>)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>Excel-style format | buil-in format name | custom format name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>step</td>	<td>Specifies whether the chart is displayed as a step line.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>stepPosition</td>	<td>Configures the position of turn points for a step line chart.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>'start' | 'middle' | 'end'</td>	<td class='tcenter'>'end'</td>	</tr>
<tr>	<td>lineColor</td>	<td>Color to override default series color. Only accepts a single color.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>CSS name | hexademical | RGB | HSL</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>lineOpacity</td>	<td>% of the full color that should be rendered, with remainder being transparent</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number (0 to 1)</td>	<td class='tcenter'>1</td>	</tr>
<tr>	<td>lineType</td>	<td>Options to show breaks in a line (dashed or dotted)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>solid | dashed | dotted</td>	<td class='tcenter'>solid</td>	</tr>
<tr>	<td>lineWidth</td>	<td>Thickness of line (in pixels)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>2</td>	</tr>
<tr>	<td>markers</td>	<td>Turn on/off markers (shapes rendered onto the points of a line)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>markerShape</td>	<td>Shape to use if markers=true</td>	<td class='tcenter'>-</td>	<td class='tcenter'>circle | emptyCircle | rect | triangle | diamond</td>	<td class='tcenter'>circle</td>	</tr>
<tr>	<td>markerSize</td>	<td>Size of each shape (in pixels)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>8</td>	</tr>
<tr>	<td>colorPalette</td>	<td>Array of custom colours to use for the chart<br/>E.g., ['#cf0d06','#eb5752','#e88a87']<br/> Note that the array must be surrounded by curly braces.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>array of color strings (CSS name | hexademical | RGB | HSL)</td>	<td class='tcenter'>built-in color palette</td>	</tr>
</table>

### Value Labels

<table>						 
<tr>	<th class='tleft'>Name</th>	<th class='tleft'>Description</th>	<th>Required?</th>	<th>Options</th>	<th>Default</th>	</tr>
<tr>	<td>labels</td>	<td>Show value labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>labelSize</td>	<td>Font size of value labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>11</td>	</tr>
<tr>	<td>labelPosition</td>	<td>Where label will appear on your series</td>	<td class='tcenter'>-</td>	<td class='tcenter'>above | middle | below</td>	<td class='tcenter'>above</td>	</tr>
<tr>	<td>labelColor</td>	<td>Font color of value labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>CSS name | hexademical | RGB | HSL</td>	<td class='tcenter'>Automatic based on color contrast of background</td>	</tr>
<tr>	<td>labelFmt</td>	<td>Format to use for value labels (<a href='/core-concepts/formatting'>see available formats</a>)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>Excel-style format | buil-in format name | custom format name</td>	<td class='tcenter'>same as y column</td>	</tr>
<tr>	<td>yLabelFmt</td>	<td>Format to use for value labels for series on the y axis. Overrides any other formats (<a href='/core-concepts/formatting'>see available formats</a>)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>Excel-style format | buil-in format name | custom format name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>y2LabelFmt</td>	<td>Format to use for value labels for series on the y2 axis. Overrides any other formats (<a href='/core-concepts/formatting'>see available formats</a>)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>Excel-style format | buil-in format name | custom format name</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>showAllLabels</td>	<td>Allow all labels to appear on chart, including overlapping labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
</table>

### Axes

<table>						 
<tr>	<th class='tleft'>Name</th>	<th class='tleft'>Description</th>	<th>Required?</th>	<th>Options</th>	<th>Default</th>	</tr>
<tr>	<td>yLog</td>	<td>Whether to use a log scale for the y-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>yLogBase</td>	<td>Base to use when log scale is enabled</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>10</td>	</tr>
<tr>	<td>xAxisTitle</td>	<td>Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | string | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>yAxisTitle</td>	<td>Name to show beside y-axis. If 'true', formatted column name is used.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | string | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>y2AxisTitle</td>	<td>Name to show beside y2 axis. If 'true', formatted column name is used.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | string | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>xGridlines</td>	<td>Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>yGridlines</td>	<td>Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true</td>	</tr>
<tr>	<td>y2Gridlines</td>	<td>Turns on/off gridlines extending from y2-axis tick marks (horizontal lines when swapXY=false)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true</td>	</tr>
<tr>	<td>xAxisLabels</td>	<td>Turns on/off value labels on the x-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true</td>	</tr>
<tr>	<td>yAxisLabels</td>	<td>Turns on/off value labels on the y-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true</td>	</tr>
<tr>	<td>y2AxisLabels</td>	<td>Turns on/off value labels on the y2-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true</td>	</tr>
<tr>	<td>xBaseline</td>	<td>Turns on/off thick axis line (line appears at y=0)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true</td>	</tr>
<tr>	<td>yBaseline</td>	<td>Turns on/off thick axis line (line appears directly alongside the y-axis labels)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>y2Baseline</td>	<td>Turns on/off thick axis line (line appears directly alongside the y2-axis labels)</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>xTickMarks</td>	<td>Turns on/off tick marks for each of the x-axis labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>yTickMarks</td>	<td>Turns on/off tick marks for each of the y-axis labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>y2TickMarks</td>	<td>Turns on/off tick marks for each of the y2-axis labels</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>false</td>	</tr>
<tr>	<td>yMin</td>	<td>Starting value for the y-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>yMax</td>	<td>Maximum value for the y-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>y2Min</td>	<td>Starting value for the y2-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>y2Max</td>	<td>Maximum value for the y2-axis</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>yAxisColor</td>	<td>Turns on/off color on the y-axis (turned on by default when secondary y-axis is used). Can also be used to set a specific color</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false <br/> color string (CSS name | hexademical | RGB | HSL)</td>	<td class='tcenter'>true when y2 used; false otherwise</td>	</tr>
<tr>	<td>y2AxisColor</td>	<td>Turns on/off color on the y2-axis (turned on by default when secondary y-axis is used). Can also be used to set a specific color</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false <br/> color string (CSS name | hexademical | RGB | HSL)</td>	<td class='tcenter'>true when y2 used; false otherwise</td>	</tr>
</table>

### Chart

<table>						 
<tr>	<th class='tleft'>Name</th>	<th class='tleft'>Description</th>	<th>Required?</th>	<th>Options</th>	<th>Default</th>	</tr>
<tr>	<td>title</td>	<td>Chart title. Appears at top left of chart.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>string</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>subtitle</td>	<td>Chart subtitle. Appears just under title.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>string</td>	<td class='tcenter'>-</td>	</tr>
<tr>	<td>legend</td>	<td>Turns legend on or off. Legend appears at top center of chart.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>true | false</td>	<td class='tcenter'>true for multiple series</td>	</tr>
<tr>	<td>chartAreaHeight</td>	<td>Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.</td>	<td class='tcenter'>-</td>	<td class='tcenter'>number</td>	<td class='tcenter'>180</td>	</tr>
</table>

## Annotations

Line charts can include [**annotations**](/components/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```html
<LineChart data="{sales_data}" x="date" y="sales">
	<ReferenceLine data="{target_data}" y="target" label="name" />
	<ReferenceArea xMin="2020-03-14" xMax="2020-05-01" />
</LineChart>
```
