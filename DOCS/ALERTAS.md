# Alertas e controlos de qualidade

## 1. Referência e estado

- Modelo de referência: Modelo_Diagnostico_Carteira_v11.3.xlsx.
- Revisão documental: 2026-11-27.
- Fontes consultadas: Instruções, Pendências, Indicadores,
  Relatorio e Distribuições técnicas.
- Estado: catálogo inicial das condições documentadas
  e observadas; auditoria das fórmulas pendente.

Este documento distingue os avisos apresentados ao utilizador
dos controlos que condicionam o cálculo dos indicadores.

A prioridade exata e os efeitos de cada combinação
de condições devem ser confirmados nas fórmulas.

## 2. Níveis de prioridade

O modelo apresenta três níveis nas pendências por posição:

### Pendência crítica

Identifica uma condição que exige resolução antes
da utilização dos resultados afetados.

As instruções determinam a resolução das pendências
críticas antes da exportação do relatório.

### Revisão recomendada

Identifica informação que necessita de confirmação
ou revisão, com as limitações correspondentes.

Uma revisão recomendada pode coexistir com a suspensão
de uma métrica específica.

### Informação complementar

Identifica informação adicional útil para a análise.

Nos exemplos consultados, surgem neste nível faltas
de TER, benchmark ou composição detalhada.

A falta de rating é descrita nas instruções como informação
complementar, salvo regra específica.

A prioridade final depende do conjunto de condições
da posição, e não apenas de um campo isolado.

## 3. Alertas por posição e controlos globais

O modelo apresenta controlos globais relacionados com:

- Capacidade de títulos e saldos.
- Títulos ou saldos negativos.
- Apuramento de valor ou data incompleto.
- Número de pendências críticas por posição.
- Suspensão de rácios com denominador comprometido.
- Suspensão de métricas de risco da carteira.

Um contador de zero pendências críticas por posição
não comprova que estes controlos estejam resolvidos.

A relação exata entre cada controlo e os indicadores
suspensos deve ser auditada.

## 4. Catálogo inicial de situações

| Situação | Consequência a acompanhar | Como resolver |
|---|---|---|
| Data da carteira ausente ou inválida | Compromete cálculos dependentes da data e a leitura do relatório | Confirmar e preencher a data de referência |
| Título sem valor em EUR | Valor apurado e denominadores podem estar incompletos | Recuperar a valorização e a sua origem |
| Saldo sem contravalor confirmado | Liquidez e valor total podem estar incompletos | Confirmar saldo, moeda e conversão |
| Identificação ambígua do instrumento | Classificação e dados associados exigem revisão | Confirmar ISIN ou código e correspondência na base |
| Diferença de reconciliação | Apuramento não coincide com a referência disponível | Investigar posições, saldos, sobreposições e conversões |
| Exposição sem choque aplicável | Impacto total do stress indisponível | Confirmar classificação e definir o pressuposto aplicável |
| Composição inválida ou incoerente | Detalhe fica pendente ou limitado ao que é elegível | Rever pesos, categorias, datas e fontes |
| Termos de obrigação insuficientes | Fluxos ou métricas podem ficar indisponíveis | Confirmar os dados contratuais necessários |
| Preço ou métrica sem data confirmada | Atualidade não confirmada | Recuperar a data correta e a fonte |
| Capacidade excedida | A análise pode não abranger todos os registos | Tratar o excedente explicitamente e rever os limites |

Esta tabela descreve o tratamento de referência.
Não atribui uma prioridade fixa a todas as situações
sem confirmação das regras implementadas.

## 5. Reconciliação

A folha Pendências compara títulos, liquidez e carteira
com as referências disponíveis.

A tolerância apresentada no modelo é de 0,05 EUR
por componente.

Distinguir:

- Diferença dentro da tolerância.
- Diferença acima da tolerância.
- Ausência de referência comparável.

“Sem referência comparável” não equivale
a “reconciliação confirmada”.

As diferenças devem ser investigadas sem ajustamentos
artificiais destinados apenas a fechar os totais.

## 6. Zeros, dados ausentes e âmbito

Um saldo explicitamente igual a zero deve ser preservado
como zero confirmado. As instruções indicam que esse saldo
não exige taxa de câmbio.

Uma variação ou um P/L negativo não é o mesmo
que uma posição ou saldo negativo.

O âmbito documentado é de posições longas.
Títulos ou saldos negativos exigem revisão do âmbito
e dos resultados afetados.

Registos existentes nas bases técnicas sem uma posição
na carteira não devem ser confundidos com posições
efetivamente detidas.

O tratamento destas situações deve integrar os testes.

## 7. Composição de fundos e ETF

As instruções documentam:

- Validação conjunta do último retrato elegível.
- Défices atribuídos a Não classificado.
- Normalização de excessos dentro da tolerância.
- Duplicados e excessos maiores mantidos como pendentes.

A tolerância apresentada para excesso acima de 100%
é 0,005 em fração, equivalente a 0,5 pontos percentuais.

No modo GERAL, o Peso em branco é a forma de preenchimento
prevista e não deve ser confundido com a falta de um peso
necessário ao modo DETALHADO.

Uma composição parcial não determina, por si só,
uma prioridade única para toda a posição.

A disponibilidade do valor da posição, a classificação,
o detalhe e a cobertura do stress devem ser acompanhados
separadamente.

## 8. Preços manuais de obrigações

Um preço manual deve ter:

- ISIN.
- Preço limpo por 100 de nominal, positivo.
- Data até à data da carteira.
- Fonte identificada.

Segundo as instruções, um preenchimento manual incompleto
gera aviso e o modelo utiliza um dado original elegível,
quando disponível.

Para repor a seleção sem o preço manual, limpar os quatro
campos editáveis correspondentes, conforme as Instruções.

Confirmar sempre o preço efetivamente utilizado,
a sua origem e a atualização das métricas.

## 9. Atualidade dos dados de obrigações

Critérios descritos nas Instruções:

| Estado | Critério de referência |
|---|---|
| ATUALIZADO | Até 5 dias úteis |
| RECENTE | Fora do critério anterior, até 30 dias de calendário |
| ANTIGO | Fora dos critérios anteriores, até 90 dias de calendário |
| DESATUALIZADO | Mais de 90 dias de calendário |
| DATA NÃO CONFIRMADA | Data ausente ou inválida |

Os dias úteis contam segunda a sexta, sem calendário
de feriados.

Datas de preços posteriores à data da carteira
são rejeitadas segundo as instruções.

Preço, YTM publicada e duration publicada podem ter
fontes e datas distintas.

Dados antigos podem integrar uma perspetiva indicativa,
com a respetiva limitação identificada.

Os limites exatos e a ordem de avaliação devem
ser confirmados nas fórmulas.

## 10. Fluxos e pagamentos condicionais

Fluxos sem termos suficientes não devem ser apresentados
como pagamentos confirmados.

A remuneração condicional só deve entrar como confirmada
quando existir evidência documental.

A ausência de fluxo calculável deve ser distinguida
da confirmação de que não existe pagamento.

Cada moeda deve manter a sua própria soma,
salvo conversão explícita.

## 11. Conteúdo de uma pendência

A folha Pendências permite acompanhar:

- Instrumento e ISIN ou código.
- Campo em revisão.
- Motivo.
- Fonte ou confirmação necessária.
- Consequência.
- Prioridade.
- Valor em EUR e peso da posição.

A mensagem deve permitir perceber o problema
e a ação necessária para o resolver.

Após a correção, recalcular o modelo e confirmar
a atualização dos indicadores e do relatório.

## 12. Verificações pendentes

- Mapear cada mensagem às células e fórmulas de origem.
- Confirmar a prioridade de cada condição e combinação.
- Identificar os indicadores afetados por cada controlo global.
- Testar zeros confirmados e campos vazios.
- Testar saldos em falta e conversões incompletas.
- Testar datas ausentes, inválidas e posteriores à referência.
- Testar composições parciais, duplicadas e acima da tolerância.
- Testar preços manuais completos e incompletos.
- Testar ausência de choque e grupos sem exposição.
- Confirmar a atualização do relatório após correção e recálculo.

Este catálogo não representa uma validação funcional
já concluída do sistema de alertas.