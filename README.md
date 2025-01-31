Autores Portugueses
===================

Este conjunto de scripts e listas foram inicialmente feitos para gerar, como
resultado, este artigo:
* http://ensinolivre.pt/?p=285

## Direção Geral do Livro

A Direção Geral do Livro, agora Direcção Geral do Livro, dos Arquivos e das
Bibliotecas, mantinha uma base de dados de autores.
Infelizmente já não o faz, mas, na directoria `dglb`, ainda se encontram dados
provenientes de lá, e, a partir deles, foi gerado o CSV
`autores-e-suas-mortes.csv`. O script `autores.py`, também naquela directoria,
faz uma melhor análise dos dados desta fonte, gerando o ficheiro `autores.csv`.

## Biblioteca Nacional

Existe também outro conjunto de scripts, que gera uma outra lista de autores,
mas com dados vindos de outra fonte, na directoria `bnp`. Mais tarde, estas
duas listas devem ser fundidas numa só. O script `bnp.sh` descarrega os dados
em bruto, que são depois processados pelo script `process-bnp.sh`. A lista
resultante de autores é a `authors.csv`.

## Wikidata

Actualmente usada apenas como fonte de informação, a execução de
`cd wikidata; bash query-autores.sh 2020` irá dar uma lista de autores que
entram em domínio público em 2020.

## Dados consolidados

O script `consolida.sh` processa as listas de cada uma das fontes (previamente
geradas), e consolida-as numa só lista, `lista-final.csv`. Visto que a fonte
Wikidata só está a ser usada para extrair autores que morreram em determinado
ano, essa fonte não é aqui considerada.

## Outras ferramentas

Neste repositório:

* `quem-morreu.sh` -- gera um csv com a lista de todos os autores que morreram
  em determinado ano. a partir dos dados consolidados (isto é, sem ter em
  consideração os dados vindos do wikidata).
* `add-wikidata.sh` -- usado para adicionar os dados do wikidata ao resultado
* do `quem-morreu.sh`. De notar que o resultado não está ordenado
  alfabeticamente.
* `autores-e-obras.sh` -- gera uma lista de obras, ordenadas por autor, a
  partir de uma lista de autores no formato do output do `quem-morreu.sh`. A
  lista é gerada em HTML.
* `sem-wikidata.sh` -- olha para uma lista de autores no wikidata para
  determinado ano, e uma lista de quem morreu em determinado ano, cria um CSV
  com a lista de que autores não figuram no wikidata.

Noutros lados:
* [Autores-Portugueses-em-DP](https://github.com/alchimista/Autores-Portugueses-em-DP)
  é um bot para gerar uma página wikipédia a partir dos dados do wikidata,
  inpirado no trabalho mais manual que era feito neste projecto.
