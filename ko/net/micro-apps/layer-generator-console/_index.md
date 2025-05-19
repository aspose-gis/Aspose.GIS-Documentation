---
title: "레이어 생성기 콘솔 애플리케이션"
type: docs
url: /ko/net/layer-generator-console
weight: 50
---

## 요약

이 콘솔 애플리케이션은 다양한 유형의 기하학적 객체를 생성하고 선택한 형식으로 저장하도록 설계되었습니다. 점, 다각형 및 폴리라인을 만들고 생성할 객체 수를 지정하며 저장을 위한 출력 형식을 선택할 수 있습니다.

## 사용법

명령 구문:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

인수:

```
-t, --type: 기하 유형입니다. 다음 중 하나: Point, Polygon, Polyline.

-c, --count: 필수 항목입니다. 생성할 객체 수입니다. 예: 15.

-f, --fileName: 필수 항목입니다. 저장할 파일 이름입니다. 파일 이름과 확장자를 지정하십시오. 예: test.json.

-o, --outputFormat: 출력 형식입니다. 지원되는 파일 형식을 여기에서 확인하십시오.

--help: 명령에 대한 도움말 정보를 표시합니다.

--version: 애플리케이션 버전 정보를 표시합니다.
```

예제 명령을 사용하여 15개의 임의 점을 생성하고 "test.json" 형식으로 파일에 저장하는 방법:

```
app.exe -t Point -c 15 -f test.json -o json
```

## 설치 및 라이선스

애플리케이션을 사용하려면 아카이브를 다운로드하여 추출해야 합니다. 아래 링크를 따르십시오.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Aspose.GIS 레이어 생성기 콘솔 애플리케이션은 무료이지만 Aspose.GIS .NET은 일반적으로 라이선스가 부여되므로 애플리케이션을 통해 라이선스를 재사용하거나 평가판 모드에서 Aspose.GIS .NET을 사용하여 애플리케이션을 평가하거나 임시 라이선스를 요청할 수 있습니다.

## 결론

기하학적 객체 생성기는 다양한 유형의 기하학 샘플을 만들고 원하는 형식으로 저장하는 데 도움이 되는 편리한 콘솔 애플리케이션입니다. 지리 공간 데이터 작업을 하고 지리 정보 시스템을 개발하는 데 유용한 도구입니다.
