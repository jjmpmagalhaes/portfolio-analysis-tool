# Plano de validação

## 1. Objetivo e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Revisão do plano: 2026-11-27.
- Primeiro âmbito: valor, liquidez, pesos e concentração.
- Estado inicial de todos os testes: NÃO EXECUTADO.

Os resultados esperados são referências calculadas
independentemente. Ainda não representam resultados
verificados no Excel.

Cada teste deve partir de uma nova cópia da carteira-base.

## 2. Preparação

Antes de executar:

1. Identificar o ficheiro e a versão utilizados.
2. Guardar uma cópia de trabalho.
3. Registar a aplicação e versão do Excel.
4. Confirmar uma data de referência válida.
5. Preencher os dados de contexto necessários.
6. Confirmar o estado dos saldos.
7. Preservar fórmulas, validações e proteções.
8. Efetuar recálculo antes de observar os resultados.

Utilizar dados fictícios.

Para este primeiro bloco, escolher instrumentos conhecidos
na base, preferencialmente ações diretas, para isolar
os cálculos de valor e concentração.

A, B, C, D e E são rótulos deste plano.
Não devem ser introduzidos como ISIN.

Ao executar, registar a correspondência entre cada rótulo
e o instrumento escolhido. A1 e A2 devem ter o mesmo ISIN;
B, C, D e E devem ter ISIN distintos.

## 3. Carteira-base

| Linha de teste | Instrumento | Valor atual EUR |
|---|---|---:|
| A1 | A — primeiro lote | 24000 |
| A2 | A — segundo lote | 6000 |
| B | B | 25000 |
| C | C | 15000 |
| D | D | 12000 |
| E | E | 8000 |
| Saldo | Liquidez em EUR | 10000 |

Preservar os dois lotes de A na transcrição.

Preencher os restantes campos necessários de forma
consistente com os instrumentos escolhidos.

Referências explícitas do extrato fictício:

- Títulos: 90000 EUR.
- Liquidez: 10000 EUR.
- Carteira: 100000 EUR.

## 4. Critérios de concentração a confirmar

Para estes testes, o critério de aceitação proposto é:

- Agregar lotes pelo mesmo ISIN no ranking.
- Preservar os lotes na informação de origem.
- Calcular o ranking sobre os investimentos.
- Apresentar a liquidez separadamente.
- Usar o valor total da carteira, incluindo liquidez,
  como denominador dos pesos.

Este critério deve ser confirmado face às fórmulas
e aos rótulos do modelo.

Se existir uma decisão de negócio diferente,
documentá-la e rever os resultados esperados
antes de avaliar o teste.

Uma divergência pode representar erro de implementação,
erro documental ou uma regra ainda por decidir.

## 5. Resultados esperados da carteira-base

| Indicador | Resultado esperado |
|---|---:|
| Valor dos títulos | 90000 EUR |
| Liquidez | 10000 EUR |
| Valor total | 100000 EUR |
| Peso da liquidez | 10% |
| Linhas de títulos transcritas | 6 |
| Instrumentos distintos por ISIN | 5 |
| Linhas de saldo | 1 |
| Valor agregado de A | 30000 EUR |
| Maior investimento por ISIN | A, com 30% |
| Top 3 por ISIN | 70000 EUR e 70% |
| Top 5 por ISIN | 90000 EUR e 90% |
| Soma dos pesos das posições e saldo | 100% |

Pesos das linhas de origem:

- A1: 24%.
- A2: 6%.
- B: 25%.
- C: 15%.
- D: 12%.
- E: 8%.
- Liquidez: 10%.

A linha individual de maior valor é B, com 25000 EUR.
O maior investimento agregado por ISIN é A, com 30000 EUR.

Esta diferença permite verificar se o ranking agrega
efetivamente os lotes.

## 6. Casos de teste

### TC01 — Carteira-base completa

Introduzir a carteira-base e as referências explícitas.

Esperado:

- Resultados da secção 5.
- Reconciliação sem diferenças.
- Preservação dos dois lotes de A.
- Coerência entre Indicadores e Relatorio.

### TC02 — Alteração da agregação por ISIN

Partir da carteira-base.

Alterar a identificação de A2 para corresponder a B,
mantendo o valor de 6000 EUR e os restantes dados coerentes.

Esperado:

- Total da carteira: 100000 EUR.
- A agregado: 24000 EUR.
- B agregado: 31000 EUR.
- Maior investimento: B, com 31%.
- Top 3: 70000 EUR e 70%.
- Top 5: 90000 EUR e 90%.

### TC03 — Alteração da ordem das linhas

Partir da carteira-base e alterar a ordem
dos registos de entrada.

Esperado:

- Mesmos totais, pesos e concentrações.
- Correspondências com as bases preservadas.
- Identificação correta das posições nas vistas de consulta.

Este teste verifica dependências indevidas
da posição física das linhas.

### TC04 — Saldo explicitamente igual a zero

Partir da carteira-base.

Alterar o saldo para zero confirmado, mantendo EUR
como moeda e o estado de saldos fornecidos.

Retirar a taxa de câmbio do saldo.
Atualizar as referências fictícias para refletir o novo saldo.

Esperado:

- Títulos: 90000 EUR.
- Liquidez: 0 EUR.
- Total: 90000 EUR.
- Peso da liquidez: 0%.
- Maior investimento: 30000 / 90000,
  aproximadamente 33,3333%.
- Top 3: 70000 / 90000, aproximadamente 77,7778%.
- Top 5: 100%.
- Ausência de uma exigência de câmbio apenas
  por o saldo confirmado ser zero.

### TC05 — Valorização em falta

Partir da carteira-base.

Limpar o valor atual em EUR de E, preservando
a identificação da posição e as referências do extrato.

Esperado:

- A posição continua identificada.
- Valores conhecidos: 82000 EUR em títulos
  e 10000 EUR em liquidez.
- Soma conhecida: 92000 EUR, com incompletude visível.
- Referência total do extrato: 100000 EUR.
- Aviso de valorização em falta.
- Rácios e métricas dependentes do denominador completo
  tratados conforme os controlos aplicáveis.
- Ausência de apresentação destes resultados
  como diagnóstico completo da carteira.

O mapeamento exato das suspensões deve ser confirmado.

### TC06 — Liquidez não fornecida

Partir da carteira-base.

Retirar a informação do saldo e identificar
o estado dos saldos como por confirmar.

Esperado:

- Ausência de pressuposto automático de saldo zero.
- Limitação de liquidez visível.
- Tratamento adequado dos indicadores afetados.
- Distinção entre informação ausente e zero confirmado.

### TC07 — Limite da reconciliação

Manter todos os valores da carteira-base.
Alterar apenas a referência explícita do total da carteira.

| Referência total | Diferença absoluta | Esperado |
|---|---:|---|
| 100000,04 EUR | 0,04 EUR | Dentro da tolerância |
| 100000,05 EUR | 0,05 EUR | No limite da tolerância |
| 100000,06 EUR | 0,06 EUR | Acima da tolerância |

O valor apurado deve continuar a ser 100000 EUR.

Este teste também deve detetar problemas de precisão
numérica na aplicação do limite de 0,05 EUR.

### TC08 — Denominador igual a zero

Partir de uma cópia da carteira-base e colocar
os valores dos títulos e do saldo em zero confirmado.

Atualizar os totais de referência para zero.

Esperado:

- Valor total: zero.
- Ausência de erros de divisão por zero.
- Pesos e concentrações percentuais tratados
  como não calculáveis com esse denominador.
- Ausência de percentagens inventadas para completar 100%.

### TC09 — Variação negativa

Partir da carteira-base.

Introduzir uma variação percentual negativa numa posição,
mantendo a quantidade e o valor atual positivos.

Esperado:

- Total e pesos inalterados.
- Ausência de classificação como posição negativa
  apenas por existir uma perda.
- P/L tratado de acordo com os dados e regras disponíveis.

A fórmula do P/L é objeto de validação própria.

### TC10 — Valor negativo fora do âmbito

Partir da carteira-base.

Alterar o valor atual de E para -8000 EUR.

Esperado:

- Deteção do valor negativo.
- Aviso sobre o âmbito de posições longas.
- Tratamento dos indicadores afetados conforme
  os controlos globais.
- Ausência de apresentação da carteira como plenamente
  compatível com o âmbito normal do modelo.

### TC11 — Instrumento por identificar

Partir da carteira-base.

Substituir a identificação de E por uma identificação
fictícia desconhecida, sem correspondência na base,
mantendo o valor de 8000 EUR.

Não introduzir um ISIN inventado.

Esperado:

- Preservação dos 8000 EUR na valorização.
- Valor total de 100000 EUR, com os restantes dados completos.
- Identificação da pendência de classificação ou correspondência.
- Ausência de atribuição automática de uma identidade
  ou classificação sem evidência.

O efeito no ranking deve respeitar o critério
que vier a ser confirmado para posições sem ISIN.

## 7. Comparação numérica

- Valores apresentados em EUR: comparar a duas casas decimais.
- Pesos: comparar as frações antes do arredondamento visual.
- Tolerância proposta para pesos: diferença absoluta
  até 0,00000001 em fração.
- Reconciliação com o extrato: aplicar o limite específico
  de 0,05 EUR documentado no modelo.

A tolerância de reconciliação não deve ser utilizada
como tolerância genérica para todas as métricas.

## 8. Registo de execução

Para cada caso, registar:

- Identificador do teste.
- Ficheiro e versão avaliados.
- Data e responsável pela execução.
- Aplicação utilizada e confirmação do recálculo.
- Dados introduzidos e alterações à carteira-base.
- Resultado esperado.
- Resultado observado.
- Estado.
- Evidência ou localização do resultado.
- Divergência encontrada e ação seguinte.

Estados permitidos neste plano:

- NÃO EXECUTADO.
- APROVADO.
- REPROVADO.
- BLOQUEADO por falta de dados, acesso ou decisão.

Exemplo de registo inicial:

| Teste | Resultado observado | Estado | Evidência |
|---|---|---|---|
| TC01 | Por preencher | NÃO EXECUTADO | Por preencher |

Um resultado esperado calculado corretamente
não significa que o teste tenha sido aprovado no Excel.

## 9. Tratamento das divergências

Quando um teste não coincide com o esperado:

1. Confirmar os dados introduzidos.
2. Confirmar o recálculo.
3. Localizar as células e fórmulas envolvidas.
4. Comparar o comportamento com a regra documentada.
5. Distinguir erro, limitação ou decisão ainda pendente.
6. Corrigir e repetir os testes afetados.

Não alterar o resultado esperado apenas para coincidir
com o comportamento observado.

Uma mudança legítima de regra deve ficar justificada
e refletida na documentação.

## 10. Blocos seguintes

Após o núcleo, preparar testes específicos para:

- Classificação geral e composição detalhada.
- Fundos mistos e ausência de dupla contagem.
- Seleção temporal de retratos de composição.
- Stress completo e com choques em falta.
- Obrigações, preços, cupões e convenções de dias.
- YTM, duration e cobertura das métricas.
- Atualidade e seleção de fontes.
- Limites de capacidade.
- Coerência do relatório após alterações e recálculo.

## 11. Primeira tarefa de execução

Executar apenas TC01 inicialmente.

Rever os resultados antes de avançar para os restantes casos.