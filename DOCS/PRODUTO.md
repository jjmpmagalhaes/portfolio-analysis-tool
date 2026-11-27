# Definição do produto

## 1. Objetivo

Desenvolver uma ferramenta de diagnóstico de carteiras
que permita organizar dados, verificar a sua qualidade
e produzir uma análise consistente para revisão profissional.

A prioridade atual é consolidar o Excel existente.
O relatório executivo será desenvolvido a partir
dos dados e resultados dessa base.

## 2. Utilizadores

Utilizador principal proposto:

- Analista ou gestor de Wealth Management que prepara
  a análise de uma carteira e uma reunião com o cliente.

O desenvolvimento inicial será acompanhado pelo autor
do projeto, que está a aprender programação e desenvolvimento
de ferramentas com apoio de IA.

A utilização por outros colegas deve ser testada
antes de assumir que o procedimento é suficientemente claro.

## 3. Problema a resolver

A preparação de uma análise exige reunir posições,
saldos e informação dos instrumentos, reconciliar valores
e interpretar dados com diferentes níveis de qualidade.

O produto deve ajudar a:

- Reduzir trabalho repetitivo.
- Identificar informação ausente ou incoerente.
- Manter critérios de cálculo e classificação consistentes.
- Tornar visíveis as fontes, os pressupostos e as limitações.
- Facilitar a revisão da carteira pelo responsável.

## 4. Base existente

A referência funcional documentada é o Excel v11.3.

Já existem funcionalidades de importação, tratamento,
classificação, concentração, composição de fundos e ETF,
obrigações, stress, pendências e relatório A4.

A existência destas funcionalidades não significa
que todas as fórmulas e situações limite estejam validadas.

A documentação técnica inicial encontra-se nesta pasta.
As verificações pendentes devem continuar identificadas.

## 5. Fluxo de utilização

1. Reunir extratos ou imagens legíveis e identificar
   a data da carteira.
2. Preencher uma cópia limpa do modelo, manualmente
   ou com assistência de IA e revisão.
3. Confirmar posições, saldos, moedas e valores.
4. Reconciliar os dados e consultar as pendências.
5. Rever indicadores, classificações e pressupostos.
6. Utilizar os resultados e o relatório A4 existente
   para apoiar a análise profissional.

A transcrição assistida não implica importação
totalmente automática ou dispensa de revisão.

## 6. Prioridade atual: consolidar o Excel

Trabalhar por blocos, começando pelo núcleo:

- Valor total e liquidez.
- Pesos das posições.
- Maior posição e Top 3 / Top 5.
- Agregação de lotes com o mesmo ISIN.
- Tratamento de valores ausentes e zeros confirmados.
- Reconciliação e indicadores dependentes dos totais.

Depois, avançar progressivamente para:

- Classificação e composição de fundos e ETF.
- Cenários de stress.
- Métricas e fluxos de obrigações.
- Coerência dos alertas e do relatório A4.

Cada bloco deve ter resultados esperados, verificações
e limitações documentadas.

## 7. Primeira entrega de consolidação

Preparar uma versão do Excel em que o núcleo indicado
na secção anterior tenha sido testado com carteiras fictícias.

A entrega deve incluir:

- Identificação da versão de referência utilizada.
- Casos de teste com resultados calculados independentemente.
- Registo dos resultados obtidos e das divergências.
- Correções efetuadas e respetiva justificação.
- Limitações e verificações ainda pendentes.

Não se deve declarar o modelo inteiro validado
por terem passado apenas os testes de um bloco.

## 8. Critérios de aceitação

Um bloco pode ser considerado entregue quando:

- Os testes previstos passam dentro das tolerâncias
  definidas para cada métrica.
- As divergências encontradas foram resolvidas ou explicadas.
- A falta de dados não é apresentada como zero confirmado.
- Os indicadores afetados por dados insuficientes
  apresentam um estado adequado.
- Os resultados são reproduzíveis após recálculo.
- A documentação corresponde ao comportamento verificado.

As tolerâncias e os exemplos concretos serão definidos
no PLANO_VALIDACAO.md.

## 9. Relatório executivo: fase seguinte

O relatório executivo deve consumir os dados, resultados
e estados produzidos pelo Excel consolidado.

O seu conteúdo previsto inclui:

- Inventário reconciliado.
- Composição e concentração.
- Exposições documentadas.
- Liquidez e recebimentos esperados.
- Stress e respetivos pressupostos.
- Pendências e limitações relevantes.
- Pontos de discussão para revisão pelo responsável.

A configuração deste relatório é uma evolução
do relatório A4 já existente.

O conteúdo, a extensão e a automatização serão definidos
numa fase própria.

## 10. Evolução tecnológica

A migração para Python e uma eventual interface
continuam como possibilidades futuras.

A escolha tecnológica deve acompanhar as necessidades
e prioridades do produto.

O exercício inicial de leitura de CSV descrito no README
é uma possibilidade de aprendizagem, sujeita a alinhamento
com a prioridade atual de consolidação do Excel.

## 11. Medição de utilidade

Durante os testes e a utilização piloto, acompanhar:

- Tempo necessário para preparar uma carteira.
- Número de intervenções manuais.
- Erros ou divergências encontrados.
- Clareza das pendências e das instruções.
- Capacidade de outro utilizador executar o procedimento.

Os valores de partida e os objetivos quantitativos
ainda devem ser definidos.