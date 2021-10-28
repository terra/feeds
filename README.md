ARTIGOS:

- A leitura do feed ocorre a cada 3 minutos aproximadamente.
- É recomendável conter os últimos n* conteúdos (novos ou atualizados) no intervalo de leitura pelo nosso robô, ordenados por data de publicação / última atualização.
* entre 10 e 20 itens funciona bem para a maioria dos casos.
- É importante que o feed esteja válido no seguinte validador, para evitar erros na leitura e interpretação (parse): https://validator.w3.org/feed/

Campos do feed:

Declarações xml e rss: tags que definem formato, versão, codificação e namespaces. Vide primeiras linhas do Feed exemplo.
```json
Channel: campos exigidos pelo formato RSS. Não utilizamos estas informações.
	|-- title: Nome do site ou categoria
	|-- description: Descrição do site ou categoria
	|-- link: Link do site ou categoria
	|-- atom:link: Link para o RSS do site ou categoria
	|-- lastBuildDate (opcional): data de última atualização do feed, no formato RFC-822. Ex: Tue, 18 May 2021 17:14:00 -0300
	| Item:
		|-- title: título do artigo
		|-- dc:creator (opcional): assinatura do artigo (nome do autor que será exibido publicamente na página)
		|-- link: url do artigo
		|-- guid: deve ser único e imutável, podendo ser um id ou um permalink (importante informar na propriedade isPermaLink). É com este campo que sabemos se criamos um artigo novo no nosso site ou atualizamos um existente
		|-- description (opcional): subtítulo do artigo, exibido na página entre o título e o corpo. Deve conter apenas texto e não deve repetir a primeira frase do corpo do artigo
		|-- category: categoria(s) do conteúdo. Pode ser uma campo com as categorias separadas por vírgula, ou usar um campo por categoria
		|-- pubDate: data de publicação/atualização do conteúdo, no formato RFC-822. Ex: Tue, 18 May 2021 17:14:00 -0300
		|-- content:encoded: corpo do artigo. O texto precisa estar sem estilos, classes ou formatações específicas do site original. Algumas formatações e tags genérias que são aceitas: <img> <strong> <b> <i> <li> <ul>. Outras tags ou formatações podem prejudicar a interpretação, serem ignorados ou causarem conflito com nosso template
		|-- media:content (opcional): contém metadados da imagem. O caminho completo deve ser informado na priopriedade url
		    |--media:credit: atribuição do copyright da imagem, mais detalhes nas "demais considerações"
			|--media:description: legenda da imagem
```

Demais considerações:

- Caso haja galeria, as imagens <media:content> devem estar dentro de um <media:group>	
- Para imagens (no media:content ou no img), é imprescindível que haja legendas e atribuições de créditos. No img, utilizar a propriedade "data-portal-copyright" para os créditos, e no media:content usar o media:credit.
- Tamanho das imagens: não tem um padrão a ser seguido. O portal redimensiona automaticamente para os diversos formatos onde a imagem pode ser exibida (cards de formatos distintos e no artigo). O importante é que as imagens tenham um tamanho razoável para estes locais e uma qualidade aceitável.
- Os elementos (parágrafos, imagens, embeds sociais) do conteúdo devem ter relação direta ao artigo, não permitindo links relacionados, patrocinados, etc.
- Embeds de redes sociais devem ter o código equivalente ao extraído na página do post na respectiva rede social.


Artigo usado para o exemplo abaixo:
https://agenciabrasil.ebc.com.br/esportes/noticia/2021-05/campeonato-brasileiro-feminino-tera-terceira-divisao-em-2022

Feed:
 ```xml
<?xml version="1.0" encoding="UTF-8" ?>
<rss xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:atom="http://www.w3.org/2005/Atom" xmlns:media="http://search.yahoo.com/mrss/" xmlns:content="http://purl.org/rss/1.0/modules/content/" version="2.0">
	<channel>
		<title>Agência Brasil</title>
		<description>Agência pública de notícias da EBC. Informações sobre política, economia, educação, direitos humanos e outros assuntos.</description>
		<link>https://agenciabrasil.ebc.com.br/</link>
		<atom:link href="https://agenciabrasil.ebc.com.br/rss.xml" rel="self" type="application/rss+xml" />
		<lastBuildDate>Tue, 18 May 2021 17:14:00 -0300</lastBuildDate>
		<item>
			<title>Campeonato Brasileiro Feminino terá terceira divisão em 2022</title>
			<dc:creator><![CDATA[Lincoln Chaves]]></dc:creator>
			<link>https://agenciabrasil.ebc.com.br/esportes/noticia/2021-05/campeonato-brasileiro-feminino-tera-terceira-divisao-em-2022</link>
			<guid isPermaLink="false">2a3f35rt5</guid>
			<description>Total de clubes nas séries A1, A2 e a nova A3 passará de 52 para 64</description>
			<category>esportes, futebol, futebol feminino</category>
			<pubDate>Tue, 18 May 2021 17:14:00 -0300</pubDate>
			<content:encoded><![CDATA[
			<p>
			A Confederação Brasileira de Futebol (CBF) anunciou nesta terça-feira (18) a criação de uma terceira divisão do Campeonato Brasileiro de Futebol Feminino para 2022, que receberá o nome de Série A3. Com a mudança, o número de clubes em torneios nacionais adultos passará de 52 para 64.
			</p>
			<p>
			"Vivemos um momento de muita maturidade das competições adultas femininas, com o aumento da competitividade entre os clubes e uma visibilidade cada dia maior. Permitindo que novas equipes ingressem no circuito nacional de competições, a divisão A3 ajudará muito no aumento do mercado de trabalho para as atletas, além de incentivar o fortalecimento das categorias de base dos clubes, que ganham um calendário maior e mais estruturado", declarou Aline Pellegrino, coordenadora de Competições Femininas da CBF, ao site oficial da entidade.
			</p>
			
			<img src="https://imagens.ebc.com.br/9Hl4dhyPyg4lCa_lGG9ZHBhiIzg=/754x0/smart/https://agenciabrasil.ebc.com.br/sites/default/files/thumbnails/image/logo_brasileiro_feminino_a_2022.jpeg?itok=-lzlsImd" alt="A3 - Terceira Divisão - Brasileiro Feminino 2022 - logo - CBF" data-portal-copyright="Thaís Magalhães/CBF/Direitos Reservados">
			
			<p>
			A Série A3 terá 32 participantes, sendo os 27 campeões estaduais, os quatro clubes mais bem colocados no ranking nacional masculino da CBF e uma equipe oriunda do estado melhor posicionado entre as federações de futebol feminino do país. O torneio será realizado em formato mata-mata, com jogos de ida e volta. Os quatro semifinalistas garantem acesso à Série A2 (segunda divisão).
			</p>
			<p>
			Os campeões estaduais que já figurem nas Séries A1 (primeira divisão) ou A2 serão substituídos pelos times que ficarem imediatamente atrás deles nos respectivos torneios. Caso alguma das equipes classificadas pelo ranking masculino da CBF desista da Série A3 ou esteja nas divisões superiores, ela dará lugar à agremiação que aparecer na sequência da lista.
			</p>
			<p>
			Com o surgimento da terceira divisão, a Série A2 também sofrerá mudanças. Atualmente com 36 clubes, o torneio terá apenas 16 participantes, como ocorre na Série A1. O formato, porém, será diferente. As equipes serão divididas em quatro grupos com quatro integrantes, que se enfrentam em dois turnos. Os dois melhores de cada chave avançam para o mata-mata, que terá partidas de ida e volta. Quatro agremiações serão rebaixadas à Série A3.
			</p>
			
			<blockquote class="twitter-tweet"><p lang="pt" dir="ltr">Mantendo a política de acelerar o desenvolvimento da modalidade, o <a href="https://twitter.com/hashtag/BrasileiraoFeminino?src=hash&amp;ref_src=twsrc%5Etfw">#BrasileiraoFeminino</a> 🇧🇷 do próximo ano movimentará 64 clubes de todo o país. Além disso, a disputa da Supercopa Feminina, que reunirá oito equipes entre as melhores classificadas no Brasileiro A-1 e A-2 de 2021. <a href="https://t.co/fOHGJysZq0">pic.twitter.com/fOHGJysZq0</a></p>&mdash; Brasileirão Feminino Neoenergia (@BRFeminino) <a href="https://twitter.com/BRFeminino/status/1394684189623078914?ref_src=twsrc%5Etfw">May 18, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
			
			<p>
			No ano que vem, a divisão de acesso reunirá os 12 times classificados às oitavas de final deste ano e que não conquistarem a promoção à primeira divisão, além dos quatro rebaixados da Série A1. Segundo a CBF, a mudança permite às equipes da Série A2 terem um calendário fixo a partir da próxima temporada.
			</p>
			<p>
			A Série A1 segue com os 16 participantes se enfrentando em turno único na primeira fase e as oito melhores campanhas avançando às oitavas de final. A diferença a partir de 2022 é que os dois últimos colocados, não mais os quatro, serão rebaixados à Série A2.
			</p>
			<p>
			Outra novidade para 2022, anunciada em fevereiro, é a Supercopa do Brasil de Futebol Feminino, que reunirá oito equipes que estejam entre as 12 mais bem colocadas da Série A1 e as quatro melhores da Série A2. A previsão é que o torneio, em formato mata-mata, ocorra entre fevereiro e março e abra a temporada.
			</p>
			]]></content:encoded>
			<media:content url="https://agenciabrasil.ebc.com.br/sites/default/files/thumbnails/image/futebol_feminino_cbf.jpg">
				<media:credit><![CDATA[Mauro Horita/CBF/Direitos Reservados]]></media:credit>
				<media:description><![CDATA[Chute em bola]]></media:description>
			</media:content>
		</item>
		<item>
			...
		</item>		
	</channel>
</rss>
.```  
