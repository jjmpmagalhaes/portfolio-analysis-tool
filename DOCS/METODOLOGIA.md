# Metodologia de análise de carteiras

## 1. Referência e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Versão do modelo: 11.3.
- Data desta revisão documental: 2026-11-27.
- Estado: documentação inicial do procedimento existente no Excel.

Este documento descreve o processo de utilização, incluindo
tarefas manuais ou assistidas por IA. A descrição de uma etapa
não significa que esteja totalmente automatizada.

A confirmação integral das fórmulas, dos alertas e dos casos
limite deve ser registada através de verificações específicas.

## 2. Objetivo e âmbito

Produzir um diagnóstico descritivo da carteira, com informação
sobre composição, concentração, exposições, obrigações,
liquidez, qualidade dos dados e cenários de stress.

O modelo utiliza EUR como moeda-base e destina-se a posições
longas em ações, obrigações, fundos, ETF, depósitos, liquidez
e outros instrumentos que possam ser classificados.

Derivados, alavancagem e produtos estruturados complexos
podem exigir análise própria.

O relatório apoia a análise e a revisão pelo responsável.

## 3. Dados de entrada

As fontes de trabalho podem incluir:

- Extratos e imagens legíveis da carteira.
- Identificação, moeda e valorização das posições.
- Quantidades, custos e variações, quando disponíveis.
- Saldos de liquidez por moeda.
- Totais explícitos de títulos, liquidez e carteira.
- Documentação oficial dos instrumentos.
- Fontes identificadas para preços e outros dados de mercado.

A data de referência da carteira deve estar identificada.
As datas dos documentos, dos preços e da consulta das fontes
devem ser distinguidas.

Um campo vazio representa informação ausente.
Um zero só deve ser registado quando estiver confirmado.

## 4. Procedimento de referência

### 4.1. Preparar a carteira

Começar com uma cópia do modelo limpo.

Se for reutilizado um ficheiro preenchido, seguir o procedimento
de limpeza indicado nas Instruções, incluindo dados da carteira,
notas e preços manuais.

Os dados reutilizáveis dos instrumentos devem ser revistos
quanto à sua aplicabilidade à data da nova carteira.

### 4.2. Transcrever posições e saldos

Registar títulos na folha Importação e saldos na folha Liquidez.

Distinguir posições efetivas, subtotais e informação auxiliar.
Confirmar sobreposições entre imagens ou extratos antes
de excluir qualquer linha.

Preservar lotes e contas distintos, mesmo quando partilham
o mesmo ISIN.

Conservar os códigos originais. Um código interno não deve
ser convertido num ISIN por suposição.

### 4.3. Tratar a valorização

Utilizar o contravalor em EUR apresentado no extrato,
quando disponível.

Quando for necessário utilizar um câmbio, identificar
a taxa, a data e a fonte.

Distinguir quantidade, nominal, preço e valor da posição.

Um preço externo usado na análise de uma obrigação não
substitui automaticamente a valorização da posição no extrato.

### 4.4. Identificar e classificar os instrumentos

Separar os dados do instrumento dos dados da posição do cliente.

Distinguir:

- Instrumento financeiro e classe de ativos.
- Moeda de cotação e exposição cambial.
- Classificação geral e composição detalhada de fundos e ETF.

Usar informação documental para preencher as bases técnicas.
Manter informação insuficiente como pendente ou não classificada.

A composição detalhada só deve ser utilizada com pesos
e fontes verificáveis. A cobertura deve acompanhar a análise.

### 4.5. Reconciliar os dados

Comparar os valores apurados com as referências explícitas
disponíveis para títulos, liquidez e carteira.

A tolerância apresentada no modelo v11.3 é de 0,05 EUR
por componente de reconciliação.

Quando não existe uma referência comparável, essa limitação
deve ficar visível. A ausência de um total de controlo não
equivale a uma reconciliação confirmada.

As diferenças devem ser investigadas e explicadas.
Os dados não devem ser ajustados artificialmente para fechar totais.

### 4.6. Calcular e analisar

Produzir os indicadores aplicáveis aos dados disponíveis:

- Valor apurado, posições e liquidez.
- Pesos e concentração.
- Distribuições e exposições.
- Métricas e fluxos de obrigações.
- Impacto dos cenários de stress.

Cada indicador deve ter definição, denominador, unidades
e tratamento de dados em falta documentados em METRICAS.md.

A agregação por ISIN para concentração não deve eliminar
os lotes ou contas preservados na transcrição.

### 4.7. Rever obrigações e stress

Nas obrigações, confirmar os termos necessários ao cálculo,
as fontes, as datas dos preços e a cobertura das métricas.

No stress, aplicar os pressupostos documentados às exposições
relevantes e identificar a cobertura do cenário.

Na configuração existente, o stress utiliza câmbios constantes.
Choques ausentes para grupos com exposição não devem ser
interpretados como choques de zero.

As regras específicas serão detalhadas em STRESS_TEST.md.

### 4.8. Rever e apresentar

Consultar Pendências e Indicadores antes de exportar o Relatorio.

O relatório deve refletir o estado dos dados, as limitações
e os indicadores indisponíveis ou suspensos.

Rever os pontos de discussão e a apresentação em A4
antes da exportação para PDF.

Após alterações, efetuar recálculo numa aplicação compatível
e verificar os resultados. Se o recálculo não tiver sido
efetuado, registar essa limitação.

## 5. Limitações operacionais documentadas

A configuração v11.3 indica capacidade para:

- 250 linhas ativas, incluindo títulos e saldos.
- 1000 retratos de composição de fundos e ETF.
- 3000 fluxos na agenda de obrigações.

Os excedentes devem ser sinalizados e tratados explicitamente.

A qualidade da análise depende da completude, atualidade
e cobertura das fontes. Estas dimensões devem ser apresentadas
separadamente.

As métricas podem ter limitações próprias, mesmo quando
a valorização total da carteira está disponível.

## 6. Validação e evolução

A migração para Python deve preservar as regras confirmadas
e documentar as alterações metodológicas.

Para validar uma funcionalidade:

1. Definir um exemplo com resultado conhecido.
2. Verificar o cálculo de forma independente.
3. Comparar com o Excel e investigar divergências.
4. Registar o resultado, o âmbito e as limitações da verificação.

A existência de uma fórmula no Excel não substitui
a verificação da sua correção.

Melhorias propostas devem ser identificadas como propostas
até serem implementadas e verificadas.