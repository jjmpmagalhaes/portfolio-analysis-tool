# Métricas da carteira

## 1. Referência e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Revisão documental: 2026-11-27.
- Fontes consultadas: Instruções, Indicadores, Relatorio
  e cabeçalhos das bases técnicas.
- Estado: definições de referência; auditoria integral
  das fórmulas e recálculo pendentes.

As expressões abaixo explicam os indicadores.
A correspondência exata com as fórmulas do Excel deve
ser confirmada antes de declarar uma funcionalidade validada.

## 2. Convenções gerais

- Os valores agregados da carteira são apresentados em EUR.
- Os pesos usam o valor total apurado, salvo indicação diferente.
- Os valores referem-se à data da carteira.
- Informação ausente é diferente de zero confirmado.
- Uma divisão exige um denominador válido e positivo.
- Dados incompletos devem acompanhar o resultado através
  de um estado, aviso ou indicador de cobertura.

## 3. Valor e liquidez

### Valor total apurado

Soma dos valores em EUR dos títulos e dos saldos incluídos.

Valor total = soma dos títulos + soma dos saldos

Se existirem posições sem valorização ou saldos por confirmar,
o valor apurado pode representar uma carteira incompleta.

### Número de posições

Contagem das posições registadas no âmbito da análise.

O relatório apresenta investimentos e saldos separadamente.
O critério exato de ativação e contagem de linhas deve
ser confirmado nas fórmulas.

Lotes distintos do mesmo ISIN não devem ser confundidos
com instrumentos distintos para efeitos de concentração.

### Liquidez em conta

Soma dos saldos de liquidez considerados, em EUR.

Peso da liquidez = liquidez em conta / valor total

A exposição económica à classe Liquidez pode também incluir
parcelas de fundos e ETF. Essa exposição não equivale,
por si só, a dinheiro imediatamente disponível em conta.

## 4. Pesos e concentração

### Peso de uma posição

Peso da posição = valor da posição em EUR / valor total

### Soma dos pesos

Soma dos pesos = soma dos pesos das posições incluídas

Uma soma próxima de 100% verifica coerência interna,
mas não comprova que todos os ativos foram transcritos.

### Concentração por ISIN

Os lotes com o mesmo ISIN são agregados para o ranking,
conforme indicado nas Instruções.

As linhas sem ISIN mantêm-se separadas.

Maior posição = maior valor agregado elegível / valor total

Top 3 = soma dos três maiores valores elegíveis / valor total

Top 5 = soma dos cinco maiores valores elegíveis / valor total

O universo elegível e os bloqueios do ranking devem
ser confirmados nas fórmulas.

Existe uma nota de “ranking por linha de investimento”
junto de indicadores identificados como “por ISIN”.
Esta diferença de redação exige verificação.

### Emitente direto e gestora ou promotor

Estas concentrações representam relações diferentes:

- Emitente direto: entidade emitente dos títulos elegíveis.
- Gestora ou promotor: entidade associada aos veículos.

O peso de cada grupo usa o valor total da carteira.
A exposição direta deve ser distinguida da exposição
a emitentes subjacentes através de fundos e ETF.

## 5. Distribuições, exposições e cobertura

### Peso de uma categoria

Peso da categoria = exposição em EUR / valor total da carteira

A exposição pode resultar de classificação direta,
classificação geral documentada ou composição detalhada.

Cada parcela deve entrar uma única vez na dimensão analisada.

### Cobertura de classificação

Cobertura = valor classificado / base aplicável à dimensão

A base aplicável deve estar identificada. Pode ser diferente
do valor total usado para apresentar o peso da categoria.

### Composição de fundos e ETF

Distinguir:

- Classificação geral do veículo.
- Composição detalhada documentada.
- Parcela não classificada.
- Informação não aplicável à dimensão.

Uma classificação geral não comprova cobertura detalhada.

A moeda de cotação deve ser distinguida da exposição cambial.

## 6. P/L não realizado estimado

O modelo apresenta uma estimativa baseada nos valores atuais
e nas variações disponíveis no extrato.

Esta estimativa pode não incluir rendimentos recebidos,
custos, fiscalidade ou posições encerradas.

Não representa necessariamente o retorno total da carteira
num determinado período.

O modelo apresenta a quantidade de posições abrangidas.

A fórmula de estimação e a prioridade entre os campos
de variação devem ser verificadas nas células do Excel.

## 7. Métricas de obrigações diretas

As métricas utilizam os termos contratuais, os fluxos,
os preços selecionados e as respetivas fontes e datas.

### Current Yield

Relaciona o cupão anual com o preço limpo.

Com taxa de cupão em decimal e preço por 100 de nominal:

Current Yield = taxa de cupão / (preço limpo / 100)

Exemplo de referência:
Cupão de 4% e preço limpo de 98 resultam em aproximadamente
4,0816% de Current Yield.

Esta métrica não incorpora a diferença entre preço de compra
e reembolso, nem equivale à YTM.

### YTM efetiva anual bruta

Taxa que iguala o preço sujo ao valor atualizado
dos fluxos futuros considerados.

Preço sujo = preço limpo + juros corridos

Expressão de referência, com montantes na mesma unidade:

Preço sujo = soma de CF_j / (1 + y)^t_j

Onde:

- CF_j é cada fluxo contratual considerado.
- y é a taxa efetiva anual.
- t_j é o número de dias até ao fluxo dividido por 365,
  segundo a base de desconto indicada no modelo.

A convenção de cálculo dos cupões é uma parametrização
distinta da base de desconto da YTM.

O método numérico efetivamente usado no Excel
deve ser confirmado.

### Duration modificada

Mede a sensibilidade local do preço a alterações da yield.

Na mesma base efetiva anual da expressão anterior:

Duration modificada =
soma de [t_j × CF_j / (1 + y)^(t_j + 1)] / preço sujo

Esta expressão deve ser confrontada com a implementação.

A aproximação de sensibilidade tem limitações para alterações
elevadas de taxas ou instrumentos com opções e fluxos variáveis.

### Maturidade média remanescente

Agrega o tempo até à maturidade das obrigações elegíveis,
ponderado pelo respetivo valor atual em EUR.

A convenção temporal e o tratamento de datas inválidas
ou já vencidas devem ser confirmados nas fórmulas.

### Agregação e cobertura

Regra de referência para uma média ponderada:

Média = soma de (valor EUR × métrica válida)
        / soma do valor EUR das posições cobertas

Cobertura = valor EUR coberto
            / valor EUR das obrigações diretas aplicáveis

Cada métrica tem a sua cobertura.

Uma média com cobertura parcial descreve a parcela abrangida.
Os filtros efetivamente utilizados devem ser auditados.

### Atualidade

O modelo distingue perspetivas indicativas
e perspetivas com dados atualizados ou recentes.

Preço, YTM publicada e duration publicada podem ter
fontes, datas e estados de atualidade distintos.

Uma métrica calculada à data da carteira com um preço antigo
continua dependente desse preço histórico.

## 8. Cupões e reembolsos

Os recebimentos são somados por data, natureza e moeda.

O modelo apresenta:

- Cupões brutos a 3, 6 e 12 meses.
- Reembolsos a 1, 3 e 5 anos.
- Cupão anual bruto anualizado, quando aplicável.

O nominal deve resultar dos dados confirmados da posição.

Montantes em moedas diferentes não devem ser somados
sem uma conversão explícita.

Pagamentos condicionais exigem confirmação documental.

Os limites das janelas temporais e a inclusão de pagamentos
na própria data de referência devem ser verificados.

## 9. Estados de apresentação

- Zero: resultado numérico efetivamente apurado.
- Não aplicável: a métrica não se aplica ao universo analisado.
- Pendente ou indisponível: faltam dados ou condições de cálculo.
- Suspenso: um controlo impede a apresentação do indicador.

A regra exata de cada estado será documentada em ALERTAS.md.

## 10. Exemplos para validação futura

### Carteira simples

Dois investimentos de 6000 e 3000 EUR e um saldo
de 1000 EUR devem produzir:

- Valor total: 10000 EUR.
- Pesos: 60%, 30% e 10%.
- Liquidez em conta: 1000 EUR e 10%.

### Cobertura parcial

Se uma métrica estiver disponível para 250 EUR
de um universo aplicável de 1000 EUR:

- Cobertura por valor: 25%.
- A média deve representar apenas as posições abrangidas.

Estes exemplos são referências de teste.
Não representam testes já executados no Excel.

## 11. Verificações pendentes

- Mapear cada indicador às células e fórmulas de origem.
- Confirmar contagens, filtros e universo dos rankings.
- Conferir a fórmula e cobertura do P/L.
- Confirmar filtros e denominadores das médias.
- Verificar seleção de preços e métricas publicadas.
- Confirmar convenções temporais e método de resolução da YTM.
- Testar dados ausentes, zeros, duplicados e situações limite.
- Registar recálculo, resultados e divergências encontradas.