<h1>Compose Charts</h1>
<hr/>

![banner](https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/banner.png?raw=true)
![mockup](https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/mokup.png?raw=true)

## Table of Contents

1. [Quick Start](#quick-start)
1. [All Charts](#documentation)
1. [Examples](#examples)
   1. Pie Chart
   2. Line Chart
   3. Row Chart
   4. Column Chart

### Gradle Setup
```gradle
repositories {
    maven("https://jitpack.io")
}

dependencies {
    implementation ("com.github.ehsannarmani:ComposeCharts:0.0.1")
}
```
### All Charts:
![mockup](https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/full_chart.png?raw=true)

## Examples:

### Pie Chart:
<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/pie1.gif?raw=true" width="300">

```kotlin
PieChart(
   modifier = Modifier.size(200.dp),
   data = listOf(
      Pie(label = "Android",data = 20.0, color = Color.Red, selectedColor = Color.Green),
      Pie(label = "Windows",data = 45.0, color = Color.Cyan, selectedColor = Color.Blue),
      Pie(label = "Linux",data = 35.0, color = Color.Gray, selectedColor = Color.Yellow),
   ),
   onPieClick = {
       println("${it.label} Clicked")
       val pieIndex = data.indexOf(it)
       data = data.mapIndexed { mapIndex, pie -> pie.copy(selected = pieIndex == mapIndex) }
   },
   selectedScale = 1.2f,
   spaceDegreeAnimEnterSpec = floatSpec,
   colorAnimEnterSpec = tween(300),
   scaleAnimEnterSpec = floatSpec,
   colorAnimExitSpec = tween(300),
   scaleAnimExitSpec = tween(300),
   spaceDegreeAnimExitSpec = tween(300),
   selectedPaddingDegree = 0f,
   style = Pie.Style.Fill
)
```

> [!NOTE]
> You can change chart style to stroke:

<div>
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/pie2.gif?raw=true" width="300">
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/pie3.gif?raw=true" width="300">
</div>
<br/>

```kotlin
PieChart(
   ...,
   spaceDegree = 7f,
   selectedPaddingDegree = 4f,
   style = Pie.Style.Stroke(width = 100f)
)
```

<hr/>

### Column Chart:
<div>
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/column1.gif?raw=true" width="300">
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/column2.gif?raw=true" width="300">
</div>
<br/>

```kotlin
ColumnChart(
    modifier= Modifier.fillMaxSize().padding(horizontal = 22.dp),
    data = listOf(
        Bars(
            label = "Jan",
            values = listOf(
               Bars.Data(label = "Linux", value = 50.0, color = Brush.verticalGradient(...)),
               Bars.Data(label = "Windows", value = 70.0, color = SolidColor(Color.Red)),
            )
        ),
        Bars(
            label = "Feb",
            values = listOf(
               Bars.Data(label = "Linux", value = 80.0, color = Brush.verticalGradient(...)),
               Bars.Data(label = "Windows", value = 60.0, color = SolidColor(Color.Red)),
            )
        ),
        ...
    ),
    barProperties = BarProperties(
        radius = Bars.Data.Radius.Rectangle(topRight = 6.dp, topLeft = 6.dp),
        spacing = 3.dp,
        strokeWidth = 20.dp
    ),
    animationSpec = spring(
        dampingRatio = Spring.DampingRatioMediumBouncy,
        stiffness = Spring.StiffnessLow
    ),
)
```

> [!NOTE]
> You set how many data you want for every bar you want:

<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/column3.gif?raw=true" width="300">

```kotlin
ColumnChart(
    data = listOf(
        Bars(
            label = "1", values = listOf(
               Bars.Data(value = 10.0, color = Color.Blue)
            )
        ),
        Bars(
            label = "2", values = listOf(
               Bars.Data(value = 20.0, color = Color.Blue)
            )
        ),
        ...
    ),
    barProperties = BarProperties(
        spacing = 1.dp,
        strokeWidth = 10.dp,
    ),
    ...
)
```

<hr/>

### Row Chart:
<div>
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/row1.gif?raw=true" width="250">
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/row2.gif?raw=true" width="250">
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/row3.gif?raw=true" width="250">
</div>
<br>


```kotlin
RowChart(
    modifier= Modifier.fillMaxSize().padding(horizontal = 22.dp),
    data = listOf(
        Bars(
            label = "Jan",
            values = listOf(
               Bars.Data(label = "Linux", value = 50.0, color = Brush.verticalGradient(...)),
               Bars.Data(label = "Windows", value = 70.0, color = SolidColor(Color.Red)),
            )
        ),
        Bars(
            label = "Feb",
            values = listOf(
               Bars.Data(label = "Linux", value = 80.0, color = Brush.verticalGradient(...)),
               Bars.Data(label = "Windows", value = 60.0, color = SolidColor(Color.Red)),
            )
        ),
        ...
    ),
    barProperties = BarProperties(
        radius = Bars.Data.Radius.Rectangle(topRight = 6.dp, topLeft = 6.dp),
        spacing = 3.dp,
        strokeWidth = 20.dp
    ),
    animationSpec = spring(
        dampingRatio = Spring.DampingRatioMediumBouncy,
        stiffness = Spring.StiffnessLow
    ),
)
```

<hr/>

### Line Chart:
<div>
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line2.gif?raw=true" width="250">
   <img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line8.gif?raw=true" width="250">
</div>
<br>

```kotlin
LineChart(
    modifier = Modifier.fillMaxSize().padding(horizontal = 22.dp),
    data = listOf(
         Line(
            label = "Windows",
            values = listOf(28.0,41.0,5.0,10.0,35.0),
            color = SolidColor(Color(0xFF23af92)),
            firstGradientFillColor = Color(0xFF2BC0A1).copy(alpha = .5f),
            secondGradientFillColor = Color.Transparent,
            strokeAnimationSpec = tween(2000, easing = EaseInOutCubic),
            gradientAnimationDelay = 1000,
            drawStyle = DrawStyle.Stroke(width = 2.dp),
         )
    ),
    animationMode = AnimationMode.Together(delayBuilder = {
        it * 500L
    }),
)
```

> [!NOTE]
> You can set gradient color for lines:

<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line7.gif?raw=true" width="250">

```kotlin
LineChart(
    data = listOf(
         Line(
            label = "Linux",
            values = listOf(28.0,41.0,5.0,10.0,35.0),
            color = Brush.radialGradient(...),
            ...
         )
    ),
    ...
)
```

> [!NOTE]
> You can add how many lines you want:

<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line1.gif?raw=true" width="250">

```kotlin
LineChart(
    data = listOf(
         Line(
            label = "Windows",
            values = listOf(...),
            color = Color.Green,
            curvedEdges = true
         ),
         Line(
            label = "Linux",
            values = listOf(...),
            color = Color.Orange,
            curvedEdges = false
         ),
         Line(
            label = "Linux",
            values = listOf(...),
            color = Color.Blue,
            curvedEdges = true
         ),
    ),
    ...
)
```

> [!NOTE]
> You can show dots and disable line edge curving:

<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line3.gif?raw=true" width="250">

```kotlin
LineChart(
    data = listOf(
         Line(
            label = "Windows",
            values = listOf(...),
            color = Color.Orange,
            curvedEdges = true,
            dotProperties = DotProperties(
                enabled = true,
                color = SolidColor(Color.White),
                strokeWidth = 4f,
                radius = 7f,
                strokeColor = SolidColor(Color.Orange),
            )
         ),
         Line(
            label = "Linux",
            values = listOf(...),
            color = Color.Cyan,
            curvedEdges = false,
            dotProperties = DotProperties(
               ...
            )
         ),
    ),
    curvedEdges = false
)
```

> [!NOTE]
> You can make chart line dashed:

<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line6.gif?raw=true" width="250">

```kotlin
LineChart(
    data = listOf(
         Line(
            label = "Windows",
            values = listOf(...),
            drawStyle = DrawStyle.Stroke(
                width = 3.dp,
                strokeStyle = StrokeStyle.Dashed(intervals = floatArrayOf(10f,10f), phase = 15f)
            )
            ...
         ),
         Line(
            label = "Linux",
            values = listOf(...),
            ...
         ),
    ),
)
```

> [!NOTE]
> You make chart fill color:

<img src="https://github.com/ehsannarmani/ComposeCharts/blob/master/assets/charts/line9.gif?raw=true" width="250">

```kotlin
LineChart(
    data = listOf(
         Line(
            label = "Windows",
            values = listOf(...),
            color = Color.Orange,
            drawStyle = DrawStyle.Fill,
            ...
         ),
    ),
)
```

## Chart Properties:

### Bar's: `BarProperties`
> Usage: In Column/Row Charts you can set bar properties with this property

#### `thickness`: determine bar width
#### `spacing`: determine space between data bars when you have more than one bar in a data, <a href='#column-chart'>example<a/>
#### `cornerRadius`: determine bar corner radius
#### `style`: determine bar style: `DrawStyle.Fill` `DrawStyle.Stroke(...)`

<hr/>

### Dots: `DotProperties`
> Usage: In Line Charts you can set data dot shape properties with this property

#### `enabled`: set false to hide them
#### `radius`: determine dot size
#### `color`: determine dot color
#### `strokeWidth`: determine dot stroke width
#### `strokeColor`: determine dot stroke color
#### `strokeStyle`: determine dot stroke style: `StrokeStyle.Normal` `StrokeStyle.Dashed(...)`
#### `animationEnabled`: set false if you want to show dots without delay and animation
#### `animationSpec`: determine dots visibility animation spec

<hr/>

### Indicators: `IndicatorProperties`
> Usage: In every chart you can set properties of counters next to the chart

#### `enabled`: set false to hide them
#### `textStyle`: determine counter style
#### `count`: determine counters count
#### `contentBuilder`: you can build counter content with this property


<hr/>

### Grid Lines: `GridProperties`
> Usage: In every chart you can set properties of grid lines

#### `enabled`: set false to hide them
#### `style`: determine grid line style: `StrokeStyle.Normal` `StrokeStyle.Dashed()`
#### `color`: determine grid line color
#### `thickness`: determine grid line width
#### `line count`: determine count of lines (set this equal to your indicators count to make lines in right position with counter)


<hr/>

### Labels: `LabelProperties`
> Usage: In every chart you can set properties of the labels (Apr, Jan, ...)

#### `enabled`: set false to hide them
#### `textStyle`: determine label textStyle
#### `verticalPadding`: determine vertical padding of labels area
#### `labels`: In line charts use this property to define chart labels

<hr/>

### Label Helpers: `LabelHelperProperties`
> Usage: In every chart you can set properties of the labels helper which positioned in top of chart

#### `enabled`: set false to hide them
#### `textStyle`: determine label helper textStyle

<hr/>

### Popups: `PopupProperties`
> Usage: In every chart you can set properties of popup which shown when user click or drag on chart

#### `enabled`: set false to hide them
#### `animationSpec`: determine popup visibility animation spec
#### `duration`: in column/row charts, determine how long the popup will be visible
#### `textSyle`: determine popup text style
#### `containerColor`: determine popup background color
#### `cornerRadius`: determine popup corner radius
#### `contentHorizontalPadding`: determine popup horizontal padding
#### `contentVerticalPadding`: determine popup vertical padding
#### `contentBuilder`: you can build popup content with this property









