# VÍDEOS:

- A leitura do feed ocorre a cada 3 minutos aproximadamente.
- É recomendável conter os últimos n* conteúdos (novos ou atualizados) no intervalo de leitura pelo nosso robô, ordenados por data de publicação / última atualização.
* entre 10 e 20 itens funciona bem para a maioria dos casos.
- É importante que o feed esteja válido no seguinte validador, para evitar erros na leitura e interpretação (parse): https://validator.w3.org/feed/

Campos do feed:

```text
Declarações xml e rss: tags que definem formato, versão, codificação e namespaces. Vide primeiras linhas do Feed exemplo.
Channel: campos exigidos pelo formato RSS. Não utilizamos estas informações.
	|-- title: Nome do canal de vídeos
	|-- description: Descrição do canal
	|-- link: Link principal do canal
	|-- lastBuildDate (opcional): data de última atualização do feed, no formato RFC-822. Ex: Thu, 28 Aug 2025 15:44:03 -0300
	| Item:
		|-- title: título do vídeo
		|-- link: url da página do vídeo
		|-- guid: deve ser único e imutável, podendo ser um id ou permalink (importante informar na propriedade isPermaLink). É com este campo que sabemos se criamos um card novo no nosso site ou atualizamos um existente
		|-- description: resumo ou transcrição do vídeo
		|-- category: categoria(s) do conteúdo. Pode ser uma campo com as categorias separadas por vírgula, ou usar um campo por categoria
		|-- dc:type: tipo do conteúdo (ex: short, entrevista, cobertura ao vivo)
		|-- pubDate: data de publicação/atualização do conteúdo, no formato RFC-822. Ex: Thu, 28 Aug 2025 15:33:06 -0300
		|-- media:content: contém metadados do vídeo
			|-- url: caminho completo do vídeo (.mp4)
			|-- type: tipo do arquivo (ex: video/mp4)
			|-- duration: duração do vídeo em segundos (opcional)
			|-- media:thumbnail: imagem de capa do vídeo
```

Demais considerações:

- A thumbnail deve estar em boa resolução e representar visualmente o conteúdo do vídeo.
- O vídeo deve estar disponível publicamente e em formato compatível (preferencialmente `.mp4`).
- A duração do vídeo deve ser informada em segundos no atributo `duration`. Informação opcional.
- O conteúdo do campo `description` deve ser textual e informativo, evitando repetições ou excesso de hashtags.
- O campo `dc:type` pode ser usado para indicar o tipo de vídeo (ex: short, entrevista, cobertura ao vivo).
- O campo `category` pode conter múltiplas categorias separadas por vírgula ou múltiplos campos `category`.

Feed de exemplo com informações fictícias:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:media="http://search.yahoo.com/mrss/" version="2.0">
	<channel>
		<title>Canal Fictício de Vídeos</title>
		<description>Distribuição de vídeos fictícios para fins de teste</description>
		<link>https://videos.exemplo.com.br/rss</link>
		<lastBuildDate>Thu, 28 Aug 2025 16:00:00 -0300</lastBuildDate>
		
		<item>
			<title>Entrevista com especialista em IA</title>
			<link>https://videos.exemplo.com.br/view/abc123</link>
			<guid isPermaLink="false">abc123</guid>
			<description>Discussão sobre os avanços da inteligência artificial em 2025.</description>
			<category>tecnologia, inteligência artificial</category>
			<dc:type>entrevista</dc:type>
			<pubDate>Thu, 28 Aug 2025 15:45:00 -0300</pubDate>
			<media:content url="https://videos.exemplo.com.br/static/medias/abc123.mp4" type="video/mp4" duration="120">
				<media:thumbnail url="https://videos.exemplo.com.br/thumbnails/abc123.jpg"/>
			</media:content>
		</item>

		<item>
			<title>Dicas de produtividade para home office</title>
			<link>https://videos.exemplo.com.br/view/xyz789</link>
			<guid isPermaLink="false">xyz789</guid>
			<description>Veja como melhorar sua produtividade trabalhando de casa.</description>
			<category>lifestyle, trabalho remoto</category>
			<dc:type>short</dc:type>
			<pubDate>Thu, 28 Aug 2025 15:30:00 -0300</pubDate>
			<media:content url="https://videos.exemplo.com.br/static/medias/xyz789.mp4" type="video/mp4" duration="90">
				<media:thumbnail url="https://videos.exemplo.com.br/thumbnails/xyz789.jpg"/>
			</media:content>
		</item>
	</channel>
</rss>
```
