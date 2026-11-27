# Classificação de ativos

## 1. Referência e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Revisão documental: 2026-11-27.
- Fontes consultadas: Instruções, Base ativos, Base Fundos ETF,
  Exposição Fundos e ETF, Indicadores e Relatorio.
- Estado: regras documentadas; auditoria das fórmulas
  e dos mapeamentos internos pendente.

Este documento distingue os conceitos de análise dos textos
e códigos utilizados internamente pelo Excel.

## 2. Instrumento financeiro

Identifica o tipo de instrumento ou veículo detido.

Vocabulário de apresentação identificado no modelo:

- Ações diretas.
- Obrigações diretas.
- Fundos.
- ETF.
- Liquidez.
- Produtos estruturados.
- Outros.
- Por classificar.

As bases podem usar textos diferentes, como Ação ou Fundo.
As correspondências com os rótulos do relatório devem
ser confirmadas antes de alterar categorias ou automatizar
o preenchimento.

## 3. Classe de ativos

Identifica a natureza económica da exposição.

Vocabulário de apresentação identificado no modelo:

- Ações.
- Obrigações.
- Liquidez.
- Alternativos.
- Imobiliário.
- Misto.
- Outros.
- Não classificado.

Instrumento financeiro e classe de ativos são campos distintos.

Exemplos conceptuais:

| Instrumento financeiro | Classe económica possível |
|---|---|
| ETF | Ações |
| Fundo | Obrigações |
| Fundo monetário | Liquidez |
| Fundo multiativos | Misto |

Cada classificação exige confirmação documental.

O setor de atividade também é uma dimensão distinta.
Um setor imobiliário não determina, por si só,
a classificação na classe de ativos Imobiliário.

## 4. Identificação e fontes

Confirmar o instrumento através do ISIN e da documentação
correspondente à classe de unidades efetivamente detida.

A folha Exposição Fundos e ETF indica esta ordem de consulta:

1. Site da gestora.
2. Factsheet ou relatório oficial.
3. KID ou prospeto.
4. Morningstar.
5. Bolsa.

Registar a fonte, a data da informação e a data da consulta,
quando disponíveis.

O nome comercial pode orientar a pesquisa, mas não comprova
sozinho a composição, a cobertura cambial ou os pesos.

Informação insuficiente deve ficar identificada como pendente.

## 5. Fundos e ETF: veículo e exposição económica

Na distribuição por instrumento, o valor pertence
ao veículo efetivamente detido.

Na distribuição económica, esse valor pode ser atribuído
às classes documentadas.

As duas distribuições são perspetivas distintas
sobre a mesma carteira.

Uma posição não deve ser somada como veículo
e novamente como subjacentes dentro do mesmo total económico.

A classificação do fundo não transforma a posição
numa obrigação ou ação direta.

## 6. Modo GERAL

Representa uma classificação geral documentada do veículo.

Segundo as instruções da tabela de composição:

- Utilizar o modo GERAL.
- Deixar o campo Peso em branco.
- Identificar a categoria, a fonte e a data.

Este modo não cria uma composição detalhada comprovada.

Uma classificação geral em Ações não confirma a distribuição
por setores, regiões ou moedas.

A cobertura geral deve ser distinguida da cobertura
da composição detalhada.

## 7. Modo DETALHADO

Representa a repartição documentada de uma dimensão.

Os pesos devem referir-se ao valor total do veículo.

Dados necessários à leitura de cada registo:

- ISIN.
- Dimensão.
- Categoria.
- Peso.
- Data de referência.
- Fonte.

Expressão de referência:

Exposição da categoria em EUR =
valor da posição em EUR × peso aplicado da categoria

Os pesos publicados, os pesos aplicados e as eventuais
transformações devem poder ser distinguidos.

## 8. Seleção e validação da composição

A folha de exposição documenta estas regras:

- Selecionar o último retrato elegível.
- Validar o retrato em conjunto.
- Atribuir défices de composição a Não classificado.
- Normalizar excessos dentro da tolerância.
- Manter duplicados e excessos maiores como pendentes.

O parâmetro apresentado para excesso acima de 100%
é 0,005 em fração, equivalente a 0,5 pontos percentuais.

A elegibilidade temporal, as chaves dos grupos,
o limite exato da tolerância e as prioridades de seleção
devem ser confirmados nas fórmulas.

As datas e fontes de composições usadas em dimensões
diferentes devem permanecer identificáveis.

## 9. Composição parcial e dupla contagem

Uma composição inferior a 100% não deve ser completada
com pesos inventados.

A parcela sem detalhe deve continuar visível.

Dentro de cada dimensão, cada parcela entra uma única vez.
As distribuições de dimensões diferentes são analisadas
separadamente.

Uma distribuição por setor não deve ser somada
a uma distribuição por região como se fossem parcelas
diferentes da carteira.

Quando a fonte apresenta exposições superiores a 100%,
confirmar o significado dos dados antes de os utilizar.
Podem exigir tratamento fora do âmbito do modelo.

## 10. Fundos mistos

Misto representa uma classe económica mista identificada.

Quando existe composição detalhada elegível, as parcelas
entram nas classes económicas correspondentes.

Exemplo de referência:

Um fundo de 10000 EUR com composição confirmada de
60% em ações e 40% em obrigações corresponde a:

- Instrumento: 10000 EUR em Fundos.
- Exposição económica: 6000 EUR em Ações
  e 4000 EUR em Obrigações.

Na perspetiva económica, o mesmo valor não deve ser
acrescentado novamente como 10000 EUR em Misto.

Quando só existe uma classificação geral em Misto,
não se deve presumir uma repartição entre classes.

## 11. Dimensões e moeda

As dimensões identificadas nas instruções e na análise
incluem classe económica, setor, região de investimento,
moeda e maturidade.

O catálogo exato de dimensões aceites e as correspondências
internas devem ser confirmado no Excel.

Na dimensão Moeda, utilizar exposição cambial documentada.

Distinguir:

- Moeda da unidade ou de cotação.
- Moeda-base do fundo.
- Existência de cobertura cambial.
- Exposição cambial dos ativos subjacentes.

A designação de uma unidade em EUR não comprova,
por si só, exposição económica integral ao euro.

## 12. Informação por classificar

Distinguir:

- Por classificar: tipo de instrumento ainda não identificado.
- Não classificado: exposição económica ou parcela sem atribuição.
- Outros: categoria identificada fora das restantes categorias.
- Não aplicável: dimensão sem aplicação à parcela analisada.

A categoria Outros não deve servir para esconder
informação desconhecida.

Uma classificação pendente não implica excluir
a posição da valorização quando o seu valor está disponível.

## 13. Verificações pendentes

- Mapear os textos das bases para os rótulos do relatório.
- Confirmar o catálogo de dimensões e categorias aceites.
- Auditar a seleção de retratos e os controlos de duplicados.
- Verificar os limites de tolerância e a normalização.
- Confirmar a articulação entre classificação geral
  e composição detalhada.
- Testar composições completas, parciais e incoerentes.
- Confirmar a reconciliação das exposições com o valor da carteira.

Os exemplos deste documento são referências de validação.
Não representam testes já executados no Excel.