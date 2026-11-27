# Metodologia do stress test

## 1. Referência e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Revisão documental: 2026-11-27.
- Fontes consultadas: Instruções, Indicadores,
  Carteira tratada e Relatorio.
- Estado: regras e parâmetros documentados;
  auditoria das fórmulas e testes funcionais pendentes.

Os valores históricos abaixo são os registados no modelo.
A sua transcrição não representa uma nova validação
das séries junto dos fornecedores dos índices.

## 2. Objetivo e interpretação

Estimar o efeito de choques definidos sobre o valor
da carteira na data de referência.

É um cenário estático: aplica pressupostos à composição
atual, mantendo os restantes elementos constantes.

O resultado não atribui uma probabilidade ao cenário
nem representa uma perda máxima garantida.

## 3. Origem dos choques de referência

O modelo utiliza os dez anos civis completos de 2016 a 2025.

As séries são apresentadas em EUR, com rendimentos
reinvestidos:

- MSCI World Net Return (EUR).
- Bloomberg Euro Aggregate Bond (EUR).

As fontes indicadas no modelo são MSCI, BlackRock
e Bloomberg, consultadas em 17/11/2026.

Para cada série, é selecionado o menor retorno anual.
No conjunto registado, ambos os mínimos ocorreram em 2022:

| Referência | Mínimo anual registado |
|---|---:|
| MSCI World Net Return (EUR) | -12,78% |
| Bloomberg Euro Aggregate Bond (EUR) | -17,17% |

Estes mínimos são escolhidos separadamente por série.
A coincidência do ano deve ser confirmada quando
a janela histórica for alterada.

Uma mudança de janela, índice ou convenção constitui
uma alteração metodológica a documentar.

## 4. Grupos e pressupostos iniciais

O quadro de Indicadores apresenta:

| Grupo de stress | Pressuposto inicial |
|---|---:|
| Ações | -12,78% |
| Obrigações | -17,17% |
| ETF de ações | -12,78% |
| ETF de obrigações | -17,17% |
| Fundos sem classe | Por definir |
| Liquidez | 0% |
| Outros | Por definir |
| Misto sem decomposição | Por definir |

Os choques podem ser ajustados nos campos editáveis
identificados a amarelo.

Um campo por preencher não equivale a um choque de zero.

O cenário utiliza câmbios constantes.

## 5. Dados necessários

- Valor da carteira e das posições em EUR.
- Classificação económica utilizável.
- Composição elegível dos fundos e ETF, quando disponível.
- Grupo de stress aplicável a cada parcela.
- Choque definido para os grupos com exposição.
- Estado dos controlos e da reconciliação.

As fontes e as datas das composições utilizadas
devem permanecer identificadas.

## 6. Aplicação às exposições

Expressões de referência:

Impacto da parcela = exposição em EUR × choque aplicável

Impacto total = soma dos impactos das parcelas

Impacto percentual = impacto total / valor da carteira

Valor após stress = valor da carteira + impacto total

Cada parcela deve entrar uma única vez no cálculo.

A afetação exata dos instrumentos e das parcelas
às linhas do quadro de stress deve ser confirmada
nas fórmulas, especialmente nos fundos e ETF.

## 7. Fundos, ETF e composição detalhada

O modelo indica aplicação de look-through
ao stress global.

Quando existe decomposição elegível, as parcelas
económicas são consideradas no cenário aplicável.

O valor do veículo não deve ser novamente somado
às parcelas já incluídas.

Uma classificação geral não comprova uma composição
detalhada. A parcela sem classificação ou sem choque
deve ficar identificada.

Para fundos mistos sem decomposição, é necessário
um pressuposto explícito para o grupo aplicável.

Os cenários setoriais e regionais referidos em Indicadores
são descritos como aplicáveis às posições diretas.
O seu alcance deve ser distinguido do stress global.

## 8. Dados ou choques em falta

As instruções e o relatório estabelecem que:

- Grupos com exposição exigem um choque aplicável.
- Uma exposição sem choque impede a apresentação
  de um impacto total completo.
- Um grupo sem exposição não exige que se invente
  um pressuposto apenas para preencher a tabela.
- Avisos sobre os dados da carteira podem suspender
  o cálculo ou a apresentação dos resultados.

Se existir um resultado apenas para a parcela coberta,
essa natureza parcial deve estar explícita.

O valor sem choque ou sem classificação deve permanecer
visível, em vez de ser tratado como exposição de impacto zero.

Os gatilhos exatos de suspensão e apresentação
serão detalhados em ALERTAS.md.

## 9. Exemplo numérico de referência

Carteira fictícia:

- Ações: 6000 EUR.
- Obrigações: 3000 EUR.
- Liquidez: 1000 EUR.
- Total: 10000 EUR.

Aplicando os pressupostos iniciais:

- Ações: 6000 × (-12,78%) = -766,80 EUR.
- Obrigações: 3000 × (-17,17%) = -515,10 EUR.
- Liquidez: 1000 × 0% = 0 EUR.

Resultado:

- Impacto total: -1281,90 EUR.
- Impacto percentual: -12,819%, ou -12,82% arredondado.
- Valor após stress: 8718,10 EUR.

A aritmética foi conferida separadamente.
Este exemplo ainda deve ser reproduzido no Excel
para validar a implementação.

## 10. Limitações

### Retorno anual e queda máxima

O pior retorno de um ano civil não mede necessariamente
a maior queda entre um pico e um mínimo dentro desse ano.

Este cenário não constitui uma medição de máximo drawdown.

### Representatividade dos índices

Os índices são referências para classes de exposição.

Um choque comum às obrigações não capta individualmente
diferenças de duration, crédito, opções ou moeda.

A correspondência entre o índice e a carteira
deve acompanhar a interpretação do resultado.

### Pressupostos constantes

A simulação não inclui automaticamente alterações
de composição, custos de negociação, fiscalidade,
liquidez de mercado ou efeitos de comportamento.

O uso de referências em EUR não substitui uma análise
específica do risco cambial de cada posição.

Instrumentos complexos ou com efeitos não lineares
podem exigir tratamento próprio.

## 11. Verificações pendentes

- Mapear os grupos de stress às fórmulas e exposições.
- Confirmar a seleção e aplicação do look-through.
- Verificar a ausência de dupla contagem.
- Confirmar os intervalos aceites para os choques editáveis.
- Testar campos vazios, zeros e grupos sem exposição.
- Testar composições parciais e classes desconhecidas.
- Confirmar os bloqueios do impacto total.
- Reproduzir o exemplo numérico no Excel.
- Verificar a atualização do relatório após recálculo.
- Rever as fontes e os valores das séries históricas.