---
title: "رسم تخطيط فورونوي"
type: docs
url: /ar/net/geo-tools/voronoi-diagram/
description: "كيفية العمل مع رسم تخطيط فورونوي باستخدام مكتبة Aspose.GIS"
weight: 70
---

# رسم تخطيط فورونوي

رسم تخطيط فورونوي هو تقسيم بسيط للمستوى: بالنظر إلى مجموعة من n نقطة (غالبًا ما يشار إليها باسم المواقع) تريد إنشاء n منطقة من المستوى، واحدة لكل نقطة. تتشكل هذه المناطق بحيث لأي موقع، أي نقطة داخل منطقته تكون أقرب إلى هذا الموقع من أي موقع آخر.

تمتلك GeoTools طريقة تسمى "MakeVoronoiGraph" لبناء رسم تخطيط فورونوي لمجموعة من النقاط. نحتاج إلى تعيين ثلاث نقاط أو أكثر، ثم نحصل على مستطيل (حساب الحد الأدنى والحد الأقصى لإحداثيات "x" و "y" لجميع النقاط) لتقييد المستوى الخاص بنا. كنتيجة لذلك، نحصل على مجموعة من الحواف التي تشكل رسم تخطيط فورونوي مقيدًا بمستطيلنا.

ثم، تمتلك GeoTools طريقة تسمى "BuildCenterline" (التي تعتمد على رسم تخطيط فورونوي) للحصول على الخط المركزي لمضلع. نحتاج إلى تعيين مضلع (أو مجموعة من النقاط) يمكن أن يحتوي على حلقات داخلية. هنا، كنتيجة لذلك، نحصل على مجموعة من الحواف التي تشكل رسم تخطيط فورونوي مقيدًا بالمضلع المدخل. هذا هو الفرق الرئيسي بين طريقتي "MakeVoronoiGraph" و "BuildCenterline". أيضًا، يمكننا تعيين مجموعة من النقاط؛ في هذه الحالة، نبني مضلعًا بهذه النقاط. في بعض الحالات، يمكننا بناء مضلع بطرق مختلفة، لذا للحصول على مزيد من الدقة، من الأفضل تعيين المضلع.

ثم تمتلك GeoTools طريقة تسمى "GetCenterlineLength" للحصول على طول الخط المركزي. هذا هو مجموع جميع حواف الخط المركزي. هنا نحتاج إلى تعيين مضلع (أو مجموعة من النقاط) يمكن أن يحتوي على حلقات داخلية.

## إنشاء رسم تخطيط فورونوي لـ 3 نقاط

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![رسم تخطيط فورونوي لـ 3 نقاط](rightTriangle.map.png)

## إنشاء رسم تخطيط فورونوي لـ 6 نقاط

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![رسم تخطيط فورونوي لـ 6 نقاط](test3.map.png)

## إنشاء رسم تخطيط فورونوي لـ 2000 نقطة عشوائية

```csharp
List<Point> sites = new List<Point>();
var extent = new Extent(0, 0, 4000, 4000);
var points = GeoGenerator.ProducePoints(extent, new PointGeneratorOptions{ Count = 2000, Seed = 1 });
foreach (Point point in points)
{ 
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![رسم تخطيط فورونوي لـ 2000 نقطة](test8.map.png)

## بناء الخط المركزي والحصول على طول الخط المركزي لمضلع مثلث قائم الزاوية

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};
Polygon polygon = new Polygon(new LinearRing(sites));
polygon = Gis.GeoTools.GeometryOperations.CloseLinearRing(polygon) as Polygon;

var edges = Gis.GeoTools.GeometryOperations.BuildCenterline(polygon);

var length = Gis.GeoTools.GeometryOperations.GetCenterlineLength(polygon);
```
![مضلع مثلث قائم الزاوية](rightTriangle_p.map.png)

## بناء الخط المركزي لمضلع مربع مع حلقة داخلية

```csharp
List<Point> exteriorSites = new List<Point>
{
    new Point(0, 300),
    new Point(300, 300),
    new Point(300, 0),
    new Point(0, 0)
};
Polygon polygon = new Polygon(new LinearRing(exteriorSites));
List<Point> interiorSites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 100),
    new Point(200, 200),
    new Point(100, 200)
};
polygon.AddInteriorRing(new LinearRing(interiorSites));
polygon = Gis.GeoTools.GeometryOperations.CloseLinearRing(polygon) as Polygon;

var edges = Gis.GeoTools.GeometryOperations.BuildCenterline(polygon);
```
![مضلع مربع](square_p_2.map.png)

## بناء الخط المركزي والحصول على طول الخط المركزي لـ 6 نقاط

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
     sites.Add(point);
}

var edges = Gis.GeoTools.GeometryOperations.BuildCenterline(sites);
var length = Gis.GeoTools.GeometryOperations.GetCenterlineLength(sites);
```
![الخط المركزي لـ 6 نقاط](test3_c.map.png)
