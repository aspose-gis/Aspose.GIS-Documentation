---
title: "Aplicativo de Console Gerador de Camadas"
type: docs
url: /pt/net/layer-generator-console
weight: 50
---

## Resumo

Este aplicativo de console é projetado para gerar objetos geométricos de vários tipos e salvá-los no formato escolhido. Ele permite criar pontos, polígonos e polilinhas, especificar o número de objetos a serem gerados e escolher o formato de saída para salvar.

## Uso

Sintaxe do comando:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumentos:

```
-t, --type: Tipo de geometria. Um dos seguintes: Point, Polygon, Polyline.

-c, --count: Obrigatório. Número de objetos a serem gerados. Por exemplo: 15.

-f, --fileName: Obrigatório. Nome do arquivo para salvar. Especifique o nome e a extensão do arquivo. Por exemplo: test.json.

-o, --outputFormat: Formato de saída. Veja os formatos de arquivo suportados aqui.

--help: Exibe informações de ajuda para o comando.

--version: Exibe as informações da versão do aplicativo.
```

Um exemplo de comando para criar 15 pontos aleatórios e salvá-los em um arquivo com o formato "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Instalação e Licenciamento

Se você deseja usar o aplicativo, precisa baixar o arquivo e extraí-lo. Por favor, siga o link abaixo.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Embora o Aplicativo de Console Gerador de Camadas Aspose.GIS seja gratuito, o Aspose.GIS .NET é licenciado normalmente, então você pode reutilizar sua licença através do aplicativo ou avaliar o aplicativo usando o Aspose.GIS .NET no modo de avaliação ou solicitar uma Licença Temporária.

## Conclusão

O Gerador de Objetos Geométricos é um aplicativo de console conveniente que ajuda a criar amostras de geometria de vários tipos e salvá-las no formato desejado. É uma ferramenta útil para trabalhar com dados geoespaciais e desenvolver sistemas de informação geográfica.
