CONTEÚDO EXTERNO:



- A leitura do feed ocorre a cada 3 minutos aproximadamente.
- É recomendável conter os últimos n* conteúdos (novos ou atualizados) no intervalo de leitura pelo nosso robô, ordenados por data de publicação / última atualização.
* entre 10 e 20 itens funciona bem para a maioria dos casos.
- É importante que o feed esteja válido no seguinte validador, para evitar erros na leitura e interpretação (parse): https://validator.w3.org/feed/



Campos do feed:



```text
Declarações xml e rss: tags que definem formato, versão, codificação e namespaces. Vide primeiras linhas do Feed exemplo.
Channel: campos exigidos pelo formato RSS. Não utilizamos estas informações.
|-- title: Nome do site ou categoria
|-- description: Descrição do site ou categoria
|-- link: Link do site ou categoria
|-- lastBuildDate (opcional): data de última atualização do feed, no formato RFC-822. Ex: Tue, 18 May 2021 17:14:00 -0300
| Item:
|-- title: título do artigo
|-- link: url do artigo
|-- guid: deve ser único e imutável, podendo ser um id ou um permalink (importante informar na propriedade isPermaLink). É com este campo que sabemos se criamos um card novo no nosso site ou atualizamos um existente
|-- category: categoria(s) do conteúdo. Pode ser uma campo com as categorias separadas por vírgula, ou usar um campo por categoria
|-- pubDate: data de publicação/atualização do conteúdo, no formato RFC-822. Ex: Tue, 18 May 2021 17:14:00 -0300
|-- enclosure: URL da imagem representativa do conteúdo que ilustrará o card
```



Demais considerações:



- Tamanho das imagens: não tem um padrão a ser seguido. O portal redimensiona automaticamente para os diversos formatos onde a imagem pode ser exibida (cards de formatos distintos e no artigo). O importante é que as imagens tenham um tamanho razoável para estes locais e uma qualidade aceitável.




Artigos usados para o exemplo abaixo:
https://agenciabrasil.ebc.com.br/saude/noticia/2022-01/covid-19-ministro-da-saude-pede-que-se-reforcem-cuidados-na-vacinacao
https://agenciabrasil.ebc.com.br/esportes/noticia/2022-01/primeira-fase-da-copa-do-brasil-tem-confrontos-definidos-por-sorteio



Feed:
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<rss xmlns:content="http://purl.org/rss/1.0/modules/content/" version="2.0">
<channel>
<title>Agência Brasil</title>
<description>Agência pública de notícias da EBC. Informações sobre política, economia, educação, direitos humanos e outros assuntos.</description>
<link>https://agenciabrasil.ebc.com.br/
<lastBuildDate>Tue, 4 Jan 2022 11:16:11 -0300</lastBuildDate>
<item>
<title>Covid-19: ministro da Saúde pede que se reforcem cuidados na vacinação</title>
<link>https://agenciabrasil.ebc.com.br/saude/noticia/2022-01/covid-19-ministro-da-saude-pede-que-se-reforcem-cuidados-na-vacinacao
<guid isPermaLink="false">5891</guid>
<category>Saúde</category>
<enclosure url="https://agenciabrasil.ebc.com.br/sites/default/files/thumbnails/image/008_1.jpg" length="1" type="image/jpeg"/>
<pubDate>Tue, 4 Jan 2022 11:15:10 -0300</pubDate>
</item>
<item>
<title>Primeira fase da Copa do Brasil tem confrontos definidos por sorteio</title>
<link>https://agenciabrasil.ebc.com.br/esportes/noticia/2022-01/primeira-fase-da-copa-do-brasil-tem-confrontos-definidos-por-sorteio
<guid isPermaLink="false">5890</guid>
<category>Esportes</category>
<enclosure url="https://agenciabrasil.ebc.com.br/sites/default/files/thumbnails/image/copa_do_brasil_primeira_fase_2022.jpeg" length="1" type="image/jpeg"/>
<pubDate>Tue, 4 Jan 2022 11:14:55 -0300</pubDate>
</item>
</channel>
</rss>
```
