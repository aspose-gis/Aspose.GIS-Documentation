---
title: "Web Tiles"
type: docs
url: /th/net/web-tiles/
weight: 40
description: ห้องสมุด GIS C# จะช่วยให้คุณทำงานกับ XYZ Tile (“Slippy Map”) ได้ โปรดดูตัวอย่างโค้ดเพื่อแสดงผลไทล์ XYZ หนึ่งรายการ และแสดงผลไทล์ XYZ ตามขอบเขตและจากโฟลเดอร์
---

## **การทำงานกับ XYZ Tiles**
XYZ Tile ("Slippy Map") เป็นแนวทางสำหรับการสร้างแผนที่บนเว็บ แผนที่โลกถูกแบ่งออกเป็นส่วนๆ ที่เรียกว่าไทล์ ไทล์ทั้งหมดจะถูกเก็บไว้ในบริการไทล์ Web Mapping Service เช่น Openstreetmaps, Google Hybrid, Bing, OpenCycleMap, Thunderforest ฯลฯ และห้องสมุด Aspose.GIS C# ช่วยให้คุณทำงานกับ XYZ Tiles ได้
### **แสดงผล xyz tile หนึ่งรายการ**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-ReadTilesFromXyzFormat-OpenStreetXyzTile.cs" >}}

![osm xyz tile](osm_tile.png)
### **แสดงผล xyz tiles ตามขอบเขต**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-ReadTilesFromXyzFormat-OpenStreetXyzTiles.cs" >}}

![osm xyz tiles](osm_tiles.png)
### **เปิด xyz tile จากโฟลเดอร์**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-ReadTilesFromXyzFormat-OpenTileFromFolder.cs" >}}
