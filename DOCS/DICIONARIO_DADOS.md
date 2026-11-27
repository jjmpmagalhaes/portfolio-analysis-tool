# Dicionário de dados

## 1. Referência e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Revisão documental: 2026-11-27.
- Âmbito: folhas e campos principais identificados no modelo.
- Estado: documentação inicial dos cabeçalhos e instruções.

Este documento não é ainda um inventário completo
de todas as células, fórmulas, tabelas e intervalos técnicos.

Os tipos, unidades e necessidades de preenchimento descritos
devem ser confrontados com as validações e fórmulas do Excel.

## 2. Convenções gerais

| Tipo de dado | Regra de referência |
|---|---|
| Identificador | Guardar como texto e preservar o valor original |
| Nome ou descrição | Texto identificativo, com origem rastreável |
| Valor monetário | Número acompanhado da moeda e da unidade |
| Percentagem | Número em formato percentual; 0,05 representa 5% |
| Data | Data válida, distinguindo referência, observação e consulta |
| Campo ausente | Manter ausente e acompanhar a limitação |
| Zero confirmado | Registar como número zero |
| Estado ou categoria | Usar os valores aceites pelo modelo |

A formatação visual não substitui a confirmação
da unidade e do significado do campo.

## 3. Mapa das folhas

| Folha | Função principal |
|---|---|
| Instruções | Contexto da carteira, orientação, pressupostos e preços manuais |
| Importação | Transcrição dos títulos apresentados no extrato |
| Liquidez | Registo dos saldos por conta e moeda |
| Base ativos | Identificação e classificação geral dos instrumentos |
| Base Obrigações | Termos, fontes, preços e métricas das obrigações |
| Base Fundos ETF | Caracterização dos veículos e dados específicos |
| Exposição Fundos e ETF | Composição por dimensão, categoria, peso e data |
| Carteira tratada | Integração dos dados da carteira e das bases |
| Posições da carteira | Vista de consulta por peso e estado |
| Indicadores | Agregações, concentrações, exposições e stress |
| Pendências | Revisões, consequências e reconciliação |
| Fluxos Obrigações | Agenda e controlos dos pagamentos calculáveis |
| Relatorio | Síntese A4 destinada a revisão e exportação |
| Distribuições técnicas | Dados de apoio aos gráficos e controlos |

As folhas calculadas devem ser atualizadas através
das entradas previstas e do recálculo.

## 4. Contexto da carteira

A folha Instruções reúne informação como:

- Referência interna da carteira.
- Data de referência.
- Responsável pela preparação ou revisão.
- Data de atualização.
- Moeda-base, definida como EUR nesta versão.
- Estado dos saldos fornecidos.
- Total explícito da carteira no extrato.
- Total explícito da liquidez no extrato.
- Notas de discussão e preços manuais.

Os totais de controlo devem resultar de referências
efetivamente apresentadas no extrato.

A data da carteira, a data de um documento e a data
de um preço representam acontecimentos diferentes.

## 5. Importação de títulos

Segundo as instruções do modelo, os campos de preenchimento
incluem A:J, N:P e as notas de origem em W.

| Coluna | Campo | Significado e cuidados |
|---|---|---|
| A | Nome | Designação apresentada no extrato |
| B | ISIN | Identificador confirmado do instrumento |
| C | Moeda | Moeda apresentada para a posição |
| D | Quantidade | Quantidade na unidade indicada pelo extrato |
| E | Custo médio | Custo na moeda e convenção do extrato |
| F | Valor atual EUR | Valorização da posição em EUR |
| G | Variação % | Variação percentual apresentada no extrato |
| H | Código original | Identificador original, mesmo quando não é ISIN |
| I | Tipo de linha | Natureza da linha; valores aceites por confirmar |
| J | Nota de revisão | Dúvidas e ações necessárias |
| N | Nominal total no extrato | Nominal total explicitamente apresentado |
| O | Origem do nominal | Origem da informação sobre o nominal |
| P | Código da plataforma | Código utilizado pela plataforma de origem |
| W | Observações de origem | Notas sobre origem, datas e sobreposições |

O subtotal explícito dos títulos é registado em R6,
conforme indicado nas Instruções.

### Cuidados de interpretação

- O valor em F já está em EUR.
- A quantidade não equivale necessariamente ao nominal.
- O custo médio não deve ser tratado como preço por 100
  de nominal sem confirmação.
- G recebe a variação percentual.
- A variação em EUR aparece nas vistas tratadas;
  não deve ser introduzida em G.
- Lotes e contas distintos devem ser preservados.
- Um ISIN ausente não deve ser inventado.

Os cabeçalhos também incluem campos de validação,
correspondência e ordenação. A sua implementação
deve ser mapeada antes de os alterar.

## 6. Liquidez

As instruções indicam preenchimento em A:F e I.

| Coluna | Campo | Significado |
|---|---|---|
| A | Descrição | Identificação do saldo e respetivo contexto |
| B | Moeda original | Moeda em que o saldo é apresentado |
| C | Valor original | Montante do saldo nessa moeda |
| D | Taxa para EUR | Conversão para EUR; confirmar orientação e fórmula |
| E | Data do câmbio | Data associada à conversão ou contravalor documentado |
| F | Fonte | Origem da informação utilizada |
| G | Valor EUR | Valor tratado em EUR |
| H | Estado | Resultado dos controlos do saldo |
| I | Contravalor EUR do extrato | Valor em EUR explicitamente fornecido |
| J | Ordem | Campo de organização interna |

Registar um saldo por moeda e conta, conforme as instruções.

A conta não aparece como campo autónomo neste cabeçalho.
O seu tratamento e identificação devem ser confirmados.

Quando existe contravalor em EUR no extrato,
as instruções determinam a sua utilização.

A prioridade entre contravalor e conversão deve
ser confirmada nas fórmulas.

Um saldo explicitamente igual a zero deve ser registado
como zero, com a moeda. Não exige taxa de câmbio.

## 7. Dados dos instrumentos

### Base ativos

Campos identificados incluem:

- ISIN e código original.
- Nome normalizado.
- Tipo de instrumento e subtipo.
- Classe económica.
- Setor e tema.
- Região e país.
- Moeda e emitente.
- Fonte e data da fonte.
- Estado e nota de validação.
- Código da plataforma e campos de correspondência.

Os rótulos internos devem ser mapeados para os rótulos
de apresentação definidos em CLASSIFICACAO_ATIVOS.md.

Correspondências ausentes ou múltiplas exigem revisão.

### Base Obrigações

Grupos de dados identificados:

| Grupo | Exemplos de campos |
|---|---|
| Termos contratuais | Cupão, frequência, maturidade e convenção de dias |
| Estrutura | Tipo de taxa, índice, spread, amortização e opções |
| Posição | Quantidade, nominal unitário, nominal total e origem |
| Preços | Preço limpo, juros corridos, datas e fontes |
| Métricas | Current Yield, YTM e duration |
| Rastreabilidade | Método, atualidade, origem e notas de validação |

Distinguir dados originais, dados manuais, dados externos
e resultados efetivamente utilizados.

Os preços manuais são introduzidos na área prevista
da folha Instruções, com ISIN, preço limpo por 100,
data e fonte.

Os campos calculados de seleção e métricas devem
ser preservados.

### Base Fundos ETF

Campos identificados incluem:

- ISIN, categoria e gestora.
- Gestão ativa ou passiva e benchmark.
- Moeda da unidade e moeda-base.
- Cobertura cambial.
- Acumulação ou distribuição.
- TER.
- Fonte e datas.
- Estado e modo de look-through.
- Dados específicos, como YTM, duration e rating,
  quando disponíveis.

Os dados publicados sobre um fundo não devem ser confundidos
com métricas calculadas para obrigações diretas.

## 8. Composição de fundos e ETF

Na folha Exposição Fundos e ETF:

| Coluna | Campo | Significado |
|---|---|---|
| A | ISIN | Instrumento a que pertence a composição |
| B | Dimensão | Aspeto analisado, como classe económica ou região |
| C | Categoria | Categoria dentro da dimensão |
| D | Peso | Peso publicado, relativo ao valor total do veículo |
| E | Data de referência | Data da composição |
| F | Fonte | Documento ou origem da composição |

A tabela contém também campos calculados, incluindo:

- Estado e validade.
- Peso aplicado.
- Exposição em EUR.
- Chaves e seleção do retrato.
- Duplicados.
- Somas e controlos de composição.

No modo GERAL, o campo Peso deve ficar em branco.
No modo DETALHADO, os pesos são necessários
para representar a composição.

A seleção e propagação do modo de look-through
devem ser confirmadas entre as folhas.

O mesmo ISIN, dimensão e categoria pode surgir
em datas diferentes. Os retratos não devem ser
misturados como se fossem uma única composição.

## 9. Carteira tratada e vistas de consulta

A Carteira tratada integra dados da transcrição,
da liquidez e das bases.

Campos identificados incluem:

- Identificação e classificação.
- Quantidade e custo médio.
- Valor atual em EUR.
- Variação em EUR e em percentagem.
- Peso.
- Grupo, choque e impacto de stress.
- Exposições económicas em EUR.
- Estado da posição e alertas.
- Referências às linhas de origem.

A folha Posições da carteira apresenta uma vista
por peso decrescente, com filtros por estado.

O campo Quantidade/Nominal pode apresentar o nominal
detido nas obrigações e o saldo na moeda original.

A posição visual de uma linha ordenada não deve
ser utilizada como identificador permanente.

## 10. Fluxos de obrigações

O cabeçalho da agenda apresenta:

| Campo | Significado |
|---|---|
| ISIN | Instrumento associado |
| Obrigação | Nome da emissão |
| Emitente | Entidade emitente |
| Data | Data do fluxo |
| Tipo de fluxo | Natureza do pagamento |
| Taxa | Taxa associada ao cálculo |
| Nominal detido | Nominal considerado |
| Valor bruto | Montante bruto na moeda do fluxo |
| Moeda | Moeda de pagamento |
| Estado | Estado de cálculo ou confirmação |
| Linha da emissão | Referência interna |
| Ordem do fluxo | Organização interna |

Um instrumento pode originar vários pagamentos.

O valor bruto do fluxo não é automaticamente um valor
em EUR. Os montantes mantêm a moeda de pagamento.

As datas contratuais, regras de dia útil e opções
devem ser verificadas na documentação da emissão.

## 11. Relações e identificação

- O ISIN identifica o instrumento, mas não identifica
  sozinho uma posição do cliente.
- Um instrumento pode aparecer em vários lotes ou contas.
- Um fundo ou ETF pode ter vários registos de composição.
- Uma emissão pode originar vários fluxos.
- As agregações para concentração não devem eliminar
  os registos de origem.

O modelo inclui referências como Linha importada,
Linha da liquidez, Linha da base e Linha da emissão.

A estabilidade destas referências perante ordenação,
inserção ou remoção de linhas deve ser testada.

## 12. Verificações pendentes

- Identificar nomes e limites das tabelas estruturadas.
- Confirmar células editáveis, fórmulas e proteções.
- Mapear os valores aceites nos campos de categoria e estado.
- Confirmar unidades dos custos, quantidades e preços.
- Confirmar orientação e prioridade das conversões cambiais.
- Mapear a origem da variação em EUR.
- Auditar correspondências por ISIN e códigos alternativos.
- Confirmar chaves de composição, posição e fluxo.
- Verificar a propagação dos dados até Indicadores e Relatorio.
- Atualizar este dicionário quando a estrutura for alterada.

Os exemplos e testes do repositório devem utilizar
dados fictícios.