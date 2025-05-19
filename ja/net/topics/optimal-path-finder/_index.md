---
title: "最適な経路探索器"
type: docs
url: /ja/net/optimal-path-finder
weight: 70
---

## 要約

道路ネットワーク上の最短経路の検索は、地図上の地点間を移動する最も効率的な方法を決定することを目的とした分析プロセスです。このツールは、複数のストップを持つ最適なルートを作成したり、異なる場所間の距離と移動時間を測定したりするのに役立ちます。各呼び出しで、当社の技術は1台または複数の車両に対して最適なルートを見つけることができます。たとえば、商品の配送のための最適なルートをドライバーが見つけたり、さまざまな乗客が自宅から職場までの最適な通勤距離を決定したりするのに役立ちます。

## アルゴリズムの機能

当社のライブラリは、地図上の2点間の最も**最適な経路**を構築する機能を備えています。主な機能は次のとおりです。

1. トレイルと障害物を考慮して地図上で最適な経路を検索します：道路だけでなく、トレイルや歩道などのオフロードパスや、最適な経路の選択に影響を与える可能性のある障害物も考慮に入れます。

2. 道路のみで最適な経路を検索する：道路でのみルートを見つける必要がある場合、この機能を提供します。これはたとえば、道路上での走行が許可されている車両にとって役立ちます。

3. 道路ごとに異なる速度を設定する：さまざまな道路に異なる速度を割り当てる機能を備えています。たとえば、主要な高速道路にはより高い速度を設定し、狭い道には低い速度を設定できます。

4. 長方形の障害物を設定する：最適な経路を構築するときに考慮する必要がある地図上に長方形の障害物を定義できます。これは、建物や湖（近似値）などの既知の障害物がある場合に役立ちます。

5. 道路の検索半径を制限する：検索時間を短縮し、特定の領域のみに焦点を合わせるために、道路の検索半径を制限できます。

6. パフォーマンスと精度の制御：アルゴリズムのパフォーマンスと精度を制御する機能を提供します。検索速度とルート構築の精度との間で望ましいバランスを実現するために微調整できます。

次に、これらの各機能の詳細な説明を提供し、そのアプリケーションの例を検討します。

## ソリューションへのアプローチ

パスファインディングは簡単なタスクではありませんが、開発コミュニティで認識されているいくつかの優れた信頼性の高いアルゴリズムがあります。

当社の実装では、修正されたLeeのアルゴリズムを使用しています。平面上にセルのグリッドがあります。開始点から、波は8方向（対角線を含む）に隣接するセルに伝播し、それぞれに到達するために必要な時間を計算します。隣接するセルには障害物または道路が含まれる場合があります。道路は異なる速度係数を持つことができます。したがって、開始セルからの各セルに到達するまでの時間を「マーク」します。目標点に到達した場合、グリッドを使用して逆パスを構築します。

道路ネットワーク上の最適な経路を決定するには、いくつかの手順を実行する必要があります。まず、道路を定義し、それぞれの移動速度を指定する必要があります。また、経路のトラバースに影響を与える可能性のある人工および自然の障害物の存在も考慮する必要があります。その後、検索の開始点と目標点を指定する必要があります。これらの予備的な手順が完了したら、実際のパスファインディングを開始できます。結果は、たとえば、一連のポイント座標として表されるパスになります。

最適な経路は、選択した輸送モードによって異なる場合があることに注意することが重要です。移動速度や障害物のセットが異なる可能性があるためです。したがって、最適な経路を検索するときに、各タイプの輸送に対して異なる道路および障害物セットを使用する必要があります。

## GitHubのデモプロジェクト

ライブラリの機能をより深く理解するために、[その使用例](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths)を検討しましょう。このコードは、パスファインディングアルゴリズムで道路と障害物を設定し、最適なルートを見つける方法を示しています。

例は次の手順で構成されています。

1. 道路情報（RoadInfo）のリストを作成します。これには、道路セグメント（Segment）と移動速度（Velocity）に関する情報が含まれます。
2. 高速道路をリストに追加します。
3. 低速な環状道路をリストに追加します。
4. Wayレイヤー生成器（WayLayerGenerator）を作成し、道路をジェネレーターに追加します。
5. 指定された半径（radius）を使用して、開始点（startPoint）から目標点（goalPoint01、goalPoint02、goalPoint03）への複数のパスを検索します。
6. 地図上に表示するための道路レイヤー（roadsLayer）を準備し、道路オブジェクトを追加します。
7. 地図上に表示するためのWayレイヤー（wayLayer）を準備し、見つかった各パスの幾何学的オブジェクトを作成します。
8. 指定されたパスに地図を保存して[表示](https://docs.aspose.com/gis/net/how-to-draw-geometry/)するShowMap関数を使用します。

このコードは、道路情報とWayレイヤー生成器を使用して、指定されたポイントの道路パスを構築および表示します。

## 検索オプション

パスファインディングは、Aspose.Gis.GeoTools.WayAnalyzer名前空間にある**WayLayerGenerator**クラスを使用して実行されます。

WayLayerGeneratorクラスには、開始点からターゲットへのパスを見つけるための**FindTheWayメソッド**があります。WayLayerGeneratorクラスのインスタンスを作成するには、WayOptionsをパラメータとして渡します（すべてのパラメータはオプションです）。

- StartPoint：開始点

- GoalPoint：目標点

- Radius：検索半径

- Scale：グリッドのスケール

- IsMoveOnlyRoad：道路のみでパスを検索するかどうか

ここで注目すべき点はScaleパラメータです。コンストラクターで指定されている場合、後続の検索に対して一定のスケールを固定します。Scaleパラメータが設定されていないがStartPointとGoalPointが設定されている場合、スケールは開始点と目標点の間の距離を100で割った値として計算されます。それ以外の場合、Scaleのデフォルト値は1です。経験豊富なユーザーにとっては、Scaleを設定するか、道路と障害物を最も効率的に表現するためにStartPointとGoalPointを直接設定する方が良いでしょう（特にそれらが多数ある場合）。

FindTheWayメソッドを使用するには、開始点と目標点を指定する必要があります。検索半径（波が伝播する距離）も設定できます。デフォルトでは、半径は開始点と目標点の間の距離に3を掛けた値として計算されます。開始点と目標点は互いに近い場合も遠い場合もあるため、それらの間の距離に基づいてグリッドのスケールを計算します。現在のスケールが前のスケールと一致しない場合は、グリッドを再計算します。Scaleパラメータを使用してスケールを固定できます。この場合、計算されず、グリッドは再計算されません。

検索を開始する前に、対応するAddRoadおよびAddBlockメソッドを使用して道路と障害物の地図を定義する必要があります。

**AddRoadメソッド**には、次のものを指定する必要があります。

- startPoint：道路の開始点

- endPoint：道路の終了点

- velocity：道路上の移動速度

**AddBlockメソッド**には、次のものを指定する必要があります。

- x：ブロックの左上隅のx座標

- y：ブロックの左上隅のy座標

- sizeX：x軸方向のサイズ

- sizeY：y軸方向のサイズ

これらのメソッドを使用すると、パスファインディングプロセスを開始する前に道路と障害物の地図を定義できます。

## コード例

道路と障害物を設定し、最適なルートを見つけるパスファインディングアルゴリズムの使用方法を示すいくつかのコード例を次に示します。

**例1**: 開始点と目標点の間のパスを見つけます。

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**例2**: Scaleパラメータを設定し、ポイントに負の座標を持たせます。

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**例3**: IsMoveOnlyRoadパラメータと検索半径を設定します。

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

**例4**: より高速な検索のためにScaleパラメータを設定します。

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**例5**: 複数の検索例。

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

これらのコード例は、道路情報とWayレイヤー生成器を使用して、指定されたポイントの道路パスを構築および表示します。

**要約すると**、最適な経路探索器は、道路ネットワークを分析し、地図上の地点間の最も効率的なルートを決定するための強力なツールです。道路の種類、障害物、さまざまな速度などのさまざまな要素を考慮して最適な経路を計算します。道路とオフロードトレイルの両方でパスを検索する機能、検索半径を制御し、パフォーマンスと精度を調整できるため、このアルゴリズムはルート最適化のための汎用性の高いソリューションを提供します。さまざまな輸送モードを考慮し、それに応じて道路および障害物セットを調整することで、配送計画や通勤の最適化など、さまざまなシナリオで使用できます。提供されているコード例と説明は、アルゴリズムの機能と使用方法を示しています。最終的に、最適な経路探索器は、道路ネットワーク内のナビゲーションを改善するための堅牢な方法を提供します。