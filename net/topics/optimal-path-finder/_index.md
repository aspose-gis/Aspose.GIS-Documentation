---
title: "Optimal Path Finder"
type: docs
url: /net/optimal-path-finder
weight: 70
---

## Summary

The search for the shortest path on a road network is a process of analysis aimed at determining the most efficient way to travel between points on a map. This tool can be useful for creating optimal routes with multiple stops or measuring the distance and travel time between different locations. With each call, our technology can find optimal routes for one or multiple vehicles. For example, it can help drivers find the optimal routes for delivering goods or determine the optimal commuting distance from home to work for different passengers.

## Algorithm Capabilities

Our library provides the ability to build the most **optimal route between two points** on a map. It has the following main features:

1. Search for the optimal path on the map, considering trails and obstacles: We take into account not only roads but also off-road paths such as trails, pedestrian walkways, and obstacles that may affect the choice of the optimal path.

2. Search for the optimal path only on roads: If you need to find a route exclusively on roads, we provide this capability. This is useful, for example, for vehicles restricted to travel only on roads.

3. Setting different speeds for roads: We have the ability to assign different speeds to different roads. For example, higher speeds can be set for major highways and lower speeds for narrow lanes.

4. Setting rectangular obstacles: You can define rectangular obstacles on the map that need to be taken into account when building the optimal path. This is useful when there are known obstacles such as buildings or lakes (their approximation).

5. Limiting the search radius for roads: You can restrict the search radius for roads to reduce search time and focus only on a specific area.

6. Performance and accuracy control: We provide the ability to control the performance and accuracy of the algorithm. You can fine-tune it to achieve the desired balance between search speed and route construction accuracy.

Next, we will provide a more detailed description of each of these features and examine examples of their applications.

## Approach to Solution

Although pathfinding is a non-trivial task, there are several good and reliable algorithms that are recognized in the development community.

In our implementation, we used a modified Lee's algorithm. We have a grid of cells on the plane. From the starting point, a wave propagates in 8 directions (including diagonals) to neighboring cells, calculating the time required to reach each of them. A neighboring cell may contain an obstacle or a road. Roads can have different velocity coefficients. Thus, we "mark" our grid with the time it takes to reach each cell from the starting cell within a certain radius or until reaching the goal point. If we reach the goal point, we build a reverse path using our grid.

To determine the optimal route on the road network, several steps need to be taken. First, you need to define the roads and specify the velocity of movement on each of them. You should also consider the presence of artificial and natural obstacles that may affect the path traversal. After that, you need to specify the starting and goal points of the search. Once these preliminary steps are done, you can proceed to the actual pathfinding. The result will be a path represented, for example, as a list of point coordinates.

It is important to note that the optimal path may depend on the chosen mode of transportation, as the speed of movement and the set of obstacles may vary. Therefore, different road and obstacle sets should be used for each type of transportation when searching for the optimal path.

## Code examples

To better understand the functionality of our library, let's consider [an example of its use](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). This code illustrates how to set up roads and obstacles in the pathfinding algorithm and find the optimal route.

The example consists of the following steps:

1. Creating a list of road information (RoadInfo), which includes information about the road segment (Segment) and the velocity of movement (Velocity).
2. Adding fast roads to the list.
3. Adding slow ring roads to the list.
4. Creating a way layer generator (WayLayerGenerator) and adding roads to the generator.
5. Searching for multiple paths from the start point (startPoint) to the goal points (goalPoint01, goalPoint02, goalPoint03) using the specified radius (radius).
6. Preparing a roads layer (roadsLayer) for display on the map and adding road objects.
7. Preparing a way layer (wayLayer) for display on the map and creating geometrical objects for each found path.
8. [Displaying the map](https://docs.aspose.com/gis/net/how-to-draw-geometry/) using the ShowMap function, saving the map at the specified path.

This code builds and displays road paths on the map for specified points using road information and the way layer generator.

## Search Options

Pathfinding is performed using the **WayLayerGenerator** class located in the Aspose.Gis.GeoTools.WayAnalyzer namespace.

The WayLayerGenerator class has the **FindTheWay method** for finding the path from the start point to the target. To create an instance of the WayLayerGenerator class, we pass the WayOptions as parameters (all parameters are optional):

- StartPoint: The start point

- GoalPoint: The target point

- Radius: The search radius

- Scale: The scale of the grid

- IsMoveOnlyRoad: Whether to search for the path only on roads

The notable feature here is the Scale parameter. If it is specified in the constructor, we fix a constant scale for subsequent searches. If the Scale parameter is not set but StartPoint and GoalPoint are set, we calculate the scale as the distance between the start and goal points divided by 100. In all other cases, the default value of Scale is 1. For experienced users, it is better to set Scale or set StartPoint and GoalPoint directly to most efficiently represent roads and obstacles on the grid (especially if there are many of them).

To use the FindTheWay method, we need to specify the start and goal points. We can also set the search radius (the distance to which the wave propagates). By default, the radius is calculated as the distance between the start and goal points multiplied by 3. The start and goal points can be close or very far from each other, so based on the distance between them, we calculate the scale of our grid. If the current scale does not match the previous one, we recalculate the grid. The scale can be fixed using the Scale parameter. In this case, it is not computed, and the grid is not recalculated.

Before starting the search, we need to define the road and obstacle map using the corresponding AddRoad and AddBlock methods of the WayLayerGenerator class.

For the **AddRoad method**, we need to specify:

- startPoint: The starting point of the road

- endPoint: The end point of the road

- velocity: The velocity of movement on the road

For the **AddBlock method**, we need to specify:

- x: The x-coordinate of the top-left corner of the block

- y: The y-coordinate of the top-left corner of the block

- sizeX: The size in the x-axis

- sizeY: The size in the y-axis

These methods allow us to define the road and obstacle map before starting the pathfinding process.

## Code examples

Here are some code examples that illustrate how to set up roads and obstacles in the pathfinding algorithm and find the optimal route.

Example 1: Finding a path between start and goal points.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Example 2**: Setting the scale parameter and having negative coordinates for the point.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Example 3**: Setting IsMoveOnlyRoad parameter and search radius.

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

**Example 4**: Setting the scale parameter for faster search.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Example 5**: Multiple search example.

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

These code examples build and display road paths on the map for specified points, using road information and way layer generator.

**In summary**, the optimal path finder is a powerful tool for analyzing road networks and determining the most efficient routes between points on a map. It takes into account various factors such as road types, obstacles, and different speeds to calculate the optimal path. With the ability to search for paths on both roads and off-road trails, as well as control the search radius and adjust performance and accuracy, this algorithm provides a versatile solution for route optimization. By considering different transportation modes and adjusting road and obstacle sets accordingly, it can be used in various scenarios such as delivery planning or commute optimization. The code examples and explanations provided demonstrate the capabilities of the algorithm and the steps involved in utilizing it. Ultimately, the optimal path finder offers a robust way to find the most efficient routes and improve navigation in a road network.

