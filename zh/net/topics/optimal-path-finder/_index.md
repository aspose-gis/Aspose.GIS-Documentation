---
title: "最佳路径查找器"
type: docs
url: /zh/net/optimal-path-finder
weight: 70
---

## 摘要

在道路网络上寻找最短路径是一个分析过程，旨在确定地图上两点之间最有效的旅行方式。此工具可用于创建具有多个停靠点的最佳路线或测量不同地点之间的距离和行驶时间。每次调用时，我们的技术可以为一辆或多辆车辆找到最佳路线。例如，它可以帮助司机找到货物交付的最佳路线，或者确定不同乘客从家到工作的最佳通勤距离。

## 算法能力

我们的库提供了构建地图上两点之间**最佳路线**的能力。它具有以下主要特点：

1.  考虑路径和障碍物在地图上搜索最佳路径：我们不仅考虑道路，还考虑越野路径，如小径、人行道以及可能影响最佳路径选择的障碍物。

2.  仅在道路上搜索最佳路径：如果您需要找到完全在道路上的路线，我们可以提供此功能。例如，对于只能在道路上行驶的车辆来说，这很有用。

3.  为不同道路设置不同的速度：我们能够为不同的道路分配不同的速度。例如，可以为主干高速公路设置更高的速度，而为狭窄车道设置更低的速度。

4.  设置矩形障碍物：您可以定义地图上的矩形障碍物，在构建最佳路径时需要考虑这些障碍物。当存在建筑物或湖泊等已知障碍物（它们的近似值）时，这很有用。

5.  限制道路的搜索半径：您可以限制道路的搜索半径以减少搜索时间并仅关注特定区域。

6.  性能和准确性控制：我们提供控制算法性能和准确性的能力。您可以对其进行微调以在搜索速度与路线构建精度之间实现所需的平衡。

接下来，我们将更详细地描述这些功能中的每一个，并检查其应用示例。

## 解决方案方法

尽管寻路是一项非平凡的任务，但开发社区中存在几种良好可靠的算法。

在我们的实施中，我们使用了修改后的李氏算法。我们在平面上有一个由单元格组成的网格。从起点开始，波以8个方向（包括对角线）传播到相邻单元格，计算到达每个单元格所需的时间。相邻单元格可能包含障碍物或道路。道路可以具有不同的速度系数。因此，我们用达到起始单元格所需的时间“标记”我们的网格，直到达到目标点为止。如果我们到达目标点，我们将使用我们的网格构建反向路径。

为了确定道路网络上的最佳路线，需要采取几个步骤。首先，您需要定义道路并指定每条道路的移动速度。您还应该考虑可能影响路径遍历的人工和自然障碍物。之后，您需要指定搜索的起点和目标点。完成这些初步步骤后，您可以开始实际的寻路。结果将表示为例如点的坐标列表的路径。

重要的是要注意，最佳路径可能取决于所选择的交通方式，因为移动速度和障碍物集合可能会有所不同。因此，在搜索最佳路径时，应针对每种类型的交通使用不同的道路和障碍物集合。

## GitHub上的演示项目

为了更好地理解我们库的功能，让我们考虑[其用法的示例](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths)。这段代码说明了如何在寻路算法中设置道路和障碍物以及找到最佳路线。

该示例包括以下步骤：

1.  创建道路信息（RoadInfo）列表，其中包括有关道路段（Segment）和移动速度（Velocity）的信息。
2.  将快速道路添加到列表中。
3.  将慢速环形道路添加到列表中。
4.  创建一个路径图层生成器（WayLayerGenerator），并将道路添加到生成器中。
5.  使用指定的半径（radius）从起点（startPoint）到目标点（goalPoint01、goalPoint02、goalPoint03）搜索多个路径。
6.  为在地图上显示准备道路图层（roadsLayer），并添加道路对象。
7.  为在地图上显示准备路径图层（wayLayer），并为每个找到的路径创建几何对象。
8.  使用ShowMap函数保存指定路径上的地图，从而[显示地图](https://docs.aspose.com/gis/net/how-to-draw-geometry/)。

这段代码构建并在地图上显示道路路径，用于指定的点，使用道路信息和路径图层生成器。

## 搜索选项

寻路是使用位于Aspose.Gis.GeoTools.WayAnalyzer命名空间中的**WayLayerGenerator**类执行的。

WayLayerGenerator类具有**FindTheWay方法**，用于查找从起点到目标点的路径。要创建WayLayerGenerator类的实例，我们需要将WayOptions作为参数传递（所有参数都是可选的）：

-   StartPoint：起点
-   GoalPoint：目标点
-   Radius：搜索半径
-   Scale：网格比例
-   IsMoveOnlyRoad：是否仅在道路上搜索路径

这里的显著特点是Scale参数。如果在构造函数中指定它，我们就固定了后续搜索的恒定比例。如果未设置Scale参数但设置了StartPoint和GoalPoint，则我们将比例计算为起点和目标点之间的距离除以100。在所有其他情况下，Scale的默认值为1。对于有经验的用户来说，最好设置Scale或直接设置StartPoint和GoalPoint，以便最有效地表示道路和障碍物（尤其是在有很多道路和障碍物的情况下）。

要使用FindTheWay方法，我们需要指定起点和目标点。我们还可以设置搜索半径（波传播的距离）。默认情况下，半径计算为起点和目标点之间的距离乘以3。起点和目标点可以彼此靠近或相距甚远，因此基于它们之间的距离，我们计算网格比例。如果当前比例与先前的比例不匹配，我们将重新计算网格。可以使用Scale参数固定比例。在这种情况下，它不会被计算，并且网格也不会被重新计算。

在开始搜索之前，我们需要使用WayLayerGenerator类的相应AddRoad和AddBlock方法定义道路和障碍物地图。

对于**AddRoad方法**，我们需要指定：

-   startPoint：道路的起点
-   endPoint：道路的终点
-   velocity：道路上的移动速度

对于**AddBlock方法**，我们需要指定：

-   x：块左上角的x坐标
-   y：块左上角的y坐标
-   sizeX：x轴的大小
-   sizeY：y轴的大小

这些方法允许我们在开始寻路过程之前定义道路和障碍物地图。

## 代码示例

以下是一些代码示例，说明如何在寻路算法中设置道路和障碍物以及找到最佳路线。

**示例1**：在起点和目标点之间寻找路径。

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**示例2**：设置比例参数并具有点的负坐标。

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**示例3**：设置IsMoveOnlyRoad参数和搜索半径。

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**示例4**：设置比例参数以加快搜索速度。

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**示例5**：多个搜索示例。

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

这些代码示例构建并在地图上显示指定点的道路路径，使用道路信息和路径图层生成器。

**总而言之**，最佳路径查找器是一个强大的工具，用于分析道路网络并确定地图上两点之间最有效的路线。它考虑了各种因素，如道路类型、障碍物和不同的速度来计算最佳路径。凭借在道路和越野小径上搜索路径的能力以及控制搜索半径和调整性能和准确性的能力，该算法为路线优化提供了一种通用的解决方案。通过考虑不同的交通方式并相应地调整道路和障碍物集合，它可以在各种场景中使用，例如交付计划或通勤优化。提供的代码示例和说明演示了该算法的功能和使用步骤。最终，最佳路径查找器提供了一种可靠的方式来找到最有效的路线并改善道路网络中的导航。