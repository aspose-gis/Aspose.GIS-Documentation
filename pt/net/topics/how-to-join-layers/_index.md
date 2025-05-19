---
title: "Como Unir Camadas Usando Geometria ou Atributo"
type: docs
url: /pt/net/how-to-join-layers
weight: 70
---

## Resumo

Em SIG, junções são um mecanismo poderoso para combinar informações de diferentes camadas com base em um atributo comum ou relacionamento espacial. As junções permitem mesclar dados de atributos de uma camada (a camada de origem) com outra camada (a camada de destino) usando um campo comum ou uma localização espacial. A primeira é a junção de dados por chave (atributo na tabela). Usando um campo comum, como uma chave exclusiva, você pode vincular registros em uma tabela com registros em outra tabela. A segunda abordagem é a junção de dados por localização (espacialmente). Suportamos ambas as abordagens e oferecemos a oportunidade de usá-las dependendo de suas necessidades.

Vamos supor que você tenha recebido dados descrevendo a porcentagem de mudança na população para diferentes distritos e deseja gerar vários mapas de crescimento populacional com base nessas informações. Embora seus dados populacionais sejam armazenados em uma tabela em seu banco de dados e compartilhem um campo comum com sua camada, você pode juntar esses dados aos seus objetos geográficos e utilizar campos adicionais para rotulagem, categorização, consulta ou análise de objetos de camada.

Normalmente, você executa junções de dados com base em um valor de campo que existe em ambas as tabelas. Os nomes dos campos não precisam necessariamente corresponder, mas os tipos de dados devem ser os mesmos - números com números, strings com strings e assim por diante. Você pode executar a junção de dados usando a ferramenta de geoprocessamento "Add Join". Ao juntar atributos, os campos unidos são adicionados dinamicamente à tabela existente. As propriedades do campo, como aliases, visibilidade e formatação numérica, são preservadas ao adicionar ou remover a junção.

## Capacidades para unir por campo chave

- Essa abordagem permite **vincular registros de diferentes tabelas** com base em um campo chave comum. Você pode especificar o campo chave a ser usado para comparação para estabelecer o relacionamento entre os registros. Isso é particularmente útil quando você precisa mesclar dados com base em um identificador ou outro atributo exclusivo.

Especificando o método para comparar dados com base no campo chave:

- Você pode definir **diferentes métodos de comparação** para o campo chave ao mesclar dados. Por exemplo, você pode optar por ter uma correspondência exata, comparar com base em um padrão ou dentro de uma faixa de valores. Isso permite uma determinação mais precisa dos relacionamentos entre os registros e dá controle sobre o processo de mesclagem de dados.

Especificando uma lista de nomes de atributos a serem mesclados:

- Ao mesclar dados, você pode especificar **atributos específicos** que devem ser mesclados. Isso permite escolher apenas os atributos necessários para mesclar e gerenciar a estrutura da tabela resultante.

## Capacidades para unir usando geometria

- Essa abordagem permite vincular dados com base em sua **localização espacial**. Você pode definir um raio de pesquisa dentro do qual os objetos geométricos mais próximos serão pesquisados ​​para mesclagem. Isso é útil quando você precisa juntar dados com base em sua posição geográfica.

Controlando o raio de busca para encontrar objetos geométricos mais próximos:

- Você pode controlar **o raio de busca** ao mesclar dados com base na localização. Ao especificar um valor de raio, você determina a distância dentro da qual os objetos mais próximos serão pesquisados ​​para mesclagem. Isso dá controle sobre quais objetos participarão do processo de mesclagem de dados com base em seu relacionamento espacial.

## Projeto de Demonstração

Para entender melhor a funcionalidade de nossa biblioteca, vamos considerar [um exemplo de seu uso](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Este código ilustra como unir camadas vetoriais por atributos ou geometria.

O código fornecido consiste em dois métodos, JoinByIndex() e JoinByCoords(), que demonstram operações de junção de dados usando uma classe LayerConstructor.

No método JoinByIndex():

- Listas de geometrias com atributos associados são criadas.

- Um objeto LayerConstructor é inicializado.

- O método cria uma camada vetorial e uma camada de geometria usando as geometrias fornecidas.

- A camada de geometria é unida com base em um identificador exclusivo ("Id") usando o método JoinLayersById().

- A camada vetorial unida resultante é retornada.

No método JoinByCoords():

- Listas de geometrias com atributos associados são criadas.

- Um objeto LayerConstructor é inicializado.

- Camadas de geometria são criadas usando as geometrias fornecidas.

- As camadas de geometria são unidas com base em coordenadas correspondentes usando o método JoinLayersByCoords().

- A camada vetorial unida resultante é retornada.

Em resumo, esses métodos mostram duas abordagens diferentes para unir dados: uma com base em um identificador exclusivo e a outra com base em coordenadas correspondentes. A classe LayerConstructor facilita essas operações de junção de dados.

## Opções de Junção para Índice

A classe JoinOptions fornece um conjunto de opções para configurar camadas de junção. Vamos nos aprofundar em cada opção:

- **JoinAttributeName**: Esta opção permite especificar o nome do atributo da camada unida cujo valor será usado na comparação da condição. Ele estabelece a conexão entre as duas camadas com base neste atributo.

- **TargetAttributeName**: Com esta opção, você pode especificar o nome do atributo da camada principal que será comparado ao atributo da camada unida. Isso ajuda a determinar os recursos correspondentes entre as camadas.

- **JoinAttributeNames**: Esta opção permite especificar uma lista de nomes de atributos que você deseja unir. Se esta lista for deixada em branco ou definida como nula, todos os atributos da camada unida serão incluídos na operação de junção. No entanto, ao selecionar nomes de atributos específicos, você pode controlar os atributos que são unidos, o que pode ser útil para otimizar o uso de memória e o tempo de processamento.

- **ConditionComparer**: Esta opção permite definir uma lógica personalizada para comparar valores de atributo entre os recursos das duas camadas. Por padrão, ele usa o comparador EqualityComparer.Default, que verifica a igualdade. No entanto, você pode fornecer seu próprio comparador personalizado que implementa IEqualityComparer para requisitos de comparação mais especializados.

- **JoinedAttributesPrefix**: Esta opção permite especificar um prefixo de string para os nomes dos atributos da camada unida. O valor padrão é "joined_", o que significa que os atributos unidos serão prefixados com "joined_" na camada unida resultante. Este prefixo ajuda a diferenciar os atributos unidos dos atributos originais da camada principal.

A classe JoinOptions fornece flexibilidade e controle sobre vários aspectos do processo de junção das camadas. Você pode especificar os atributos para unir, personalizar a lógica de comparação e definir um prefixo para os atributos unidos resultantes. Essas opções permitem adaptar a operação de junção de acordo com suas necessidades específicas e obter insights significativos das camadas mescladas.

## Opções de Junção para Geometria

A classe **JoinByGeometryOptions** representa opções para unir camadas com base na geometria. Vamos explorar a funcionalidade de cada opção:

- **Radius**: Esta opção especifica o raio dentro do qual a geometria unida será pesquisada. Ele determina a proximidade dentro da qual os recursos da camada principal serão correspondidos aos recursos da camada unida com base em seu relacionamento espacial.

- **ConditionComparer**: Esta opção permite definir uma lógica personalizada para comparar valores de atributo dos recursos das duas camadas. Por padrão, ele usa o EqualityComparer.Default, que verifica a igualdade. No entanto, você pode fornecer seu próprio comparador personalizado que implementa IEqualityComparer para requisitos de comparação mais específicos.

- **JoinedAttributesPrefix**: Esta opção permite especificar um prefixo de string para os nomes dos atributos da camada unida. O valor padrão é "joined_", o que significa que os atributos unidos serão prefixados com "joined_" na camada unida resultante. Este prefixo ajuda a diferenciar os atributos unidos dos atributos originais da camada principal.

A classe JoinByGeometryOptions fornece os meios para personalizar o processo de junção de camadas com base em seu relacionamento espacial. Ao especificar um raio de busca, você pode controlar a extensão dentro da qual as geometrias serão correspondidas. Isso permite ajustar a operação de junção com base na proximidade desejada entre os recursos. A opção de fornecer um comparador personalizado oferece flexibilidade na comparação de valores de atributo e a opção de prefixar atributos unidos ajuda a diferenciá-los na camada unida resultante.

Usando essas opções, você pode realizar mesclagem de dados consciente espacialmente e obter insights das camadas unidas que são baseados em sua proximidade espacial e valores de atributo.

## Resumo

O mecanismo de junção de dados em SIG permite combinar objetos geométricos com seus respectivos atributos de diferentes camadas. Isso fornece a capacidade de analisar e extrair informações com base em relacionamentos espaciais e de atributo dentro dos dados. As opções disponíveis permitem a personalização do processo de junção para atender aos requisitos específicos e às necessidades de análise em dados GIS.

A junção de dados facilita várias tarefas, incluindo:

- Encontrar objetos que atendam a critérios espaciais específicos, como identificar todos os edifícios dentro de um raio de 500 metros de um ponto específico.

- Combinar dados geográficos para criar uma visão geral mais abrangente e informativa de uma situação.

- Analisar valores de atributo de objetos com base em condições espaciais específicas para identificar tendências e padrões.

As opções de junção de dados permitem a configuração precisa do processo de correspondência de objetos. Essas opções incluem selecionar os atributos para unir, definir lógica personalizada para comparar valores de atributo e adicionar um prefixo aos nomes dos atributos dos dados unidos. Essas opções fornecem flexibilidade e adaptabilidade ao processo de junção, atendendo às necessidades específicas e aos objetivos da análise de dados em SIG.

O mecanismo de junção de dados desempenha um papel significativo na integração e análise de dados geográficos, produzindo uma compreensão mais abrangente da natureza espacial e de atributo dos objetos sob investigação.