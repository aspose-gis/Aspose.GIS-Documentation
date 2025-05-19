---
title: "기능"
second_title: Aspose.GIS for .NET
type: docs
url: /ko/net/features/
weight: 30
keywords: GIS C# Library, GIS C# API, Read ShapeFile in C#
description: GIS C#.NET 라이브러리 또는 API는 Shapefile, GeoJSON, FileGDB, GML, KML, SVG, PostGis, Sql Server, GeoTIFF 형식을 지원합니다. 벡터 데이터를 읽고 쓰고 변환하고 시각화하며 지오메트리를 조작하고 SRID별 공간 참조 시스템을 수행하고 조회할 수 있습니다.
---

Aspose.GIS for .NET은 일반 GIS 파일 형식으로 저장된 데이터 작업을 위한 풍부한 기능 세트를 제공합니다. 벡터 GIS 데이터를 읽고 쓸 수 있으며, GIS 파일 형식 간에 변환하고, 피처 지오메트리를 생성하고 분석하며, SVG로 맵을 렌더링할 수 있습니다.

# **지원되는 형식**
주요 지원 파일 형식은 다음과 같습니다.

- Shapefile
- GeoJSON
- ESRI File Geodatabase (FileGDB)
- Geography Markup Language (GML)
- Keyhole Markup Language (KML)
- Scalable Vector Graphics (SVG)
- Databases (PostGis, Sql Server)
- GeoTIFF

전체 목록은 [지원되는 파일 형식](/gis/ko/net/supported-file-formats/)을 참조하십시오.

# **벡터 데이터 읽기 및 쓰기**
- 벡터 데이터 읽기
  - 레이어 피처 반복
  - 인덱스로 레이어 피처 읽기
  - 벡터 레이어에 대한 메타데이터 검색
- 벡터 데이터 쓰기
  - 새 레이어 및 데이터 세트 생성
- 다중 레이어 데이터 세트로 작업
  - 기존 레이어 목록
  - 새 레이어 추가
  - 데이터 세트에서 레이어 제거
- 공간 쿼리를 빠르게 하기 위해 공간 인덱스 구축.

# **벡터 데이터 변환**
- 데이터를 지원되는 형식으로 변환
- 데이터 변환 시 재투영 수행
- 변환 중 피처 속성 조정

# **데이터 시각화**
- SVG, PNG, JPEG 또는 BMP로 맵 렌더링
- 각 지오메트리 유형에 대한 스타일 사용자 지정
- 복잡한 드로잉을 위해 여러 심볼라이저 결합
- 레이어 렌더링 규칙에 따라 피처의 시각적 표현 제어
- 피처 속성 값에 기반하여 피처의 스타일 파라미터 계산

자세한 내용은 [맵 렌더링](/gis/ko/net/map-rendering/)을 참조하십시오.

# **지오메트리 조작**
- 처음부터 포인트, 라인 및 폴리곤 생성
- 기존 지오메트리 편집
- 지도에 개체 레이블 지정.
- 비선형 지오메트리 (곡선) 구축
- 비선형 지오메트리 (곡선) 선형화
- WKT 및 WKB에서/로 지오메트리 가져오기 및 내보내기
- 계산의 정밀도 모델 제어

# **벡터 데이터 분석 수행**
- 두 지오메트리가 서로 교차하는지 확인.
- 지오메트리가 겹치는지, 가장자리를 접하는지, 교차하는지 등 지오메트리 간의 관계 테스트.
- 지오메트리 간 거리 찾기
- 지오메트리의 볼록 헐, 중심 및 버퍼 영역 계산
- 모든 지오메트리의 교집합, 합집합 또는 차이 계산.

# **공간 참조 시스템 사용**
- SRID별 공간 참조 시스템 조회
- 데이터 파일에서 SRS 정보 읽기
- 생성하는 데이터에 SRS 할당
- 개별 지오메트리 및 전체 레이어 재투영
- WKT에서 공간 참조 시스템 가져오기, WKT로 공간 참조 시스템 내보내기
