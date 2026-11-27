# Instruções do projeto

## Contexto

- Este projeto evolui uma ferramenta de diagnóstico de carteiras
  já existente em Excel.
- A base documentada é o Excel v11.3. Confirma a versão mais recente
  disponibilizada antes de analisar ou alterar o modelo.
- Distingue funcionalidades existentes no Excel, implementadas
  em Python e efetivamente validadas.
- Consulta README.md e ROADMAP.md antes de começar uma alteração.
- Se precisares de um ficheiro que não está disponível, pede-o.
  Não assumes acesso a ficheiros de outras conversas.

## Aprendizagem e comunicação

- Comunica em português de Portugal, com linguagem simples.
- O utilizador está a aprender Git, VS Code e programação.
- Explica o objetivo de cada passo e os termos novos.
- Ao orientar o utilizador, apresenta uma etapa de cada vez.
- Quando o próximo passo depender de um resultado, aguarda esse resultado.
- Ao executar trabalho autorizado, explica as alterações e como verificá-las.

## Desenvolvimento

- Trabalha numa funcionalidade pequena de cada vez.
- Aproveita as regras existentes no Excel e documenta alterações.
- Confirma as fórmulas e limitações no ficheiro de referência.
- Prefere soluções simples e dependências justificadas.
- Mantém os cálculos explícitos e reproduzíveis.

## Rigor dos dados e cálculos

- Não inventes ISIN, preços, câmbios, composições ou fontes.
- Distingue informação em falta de um zero confirmado.
- Separa instrumento financeiro de classe de ativos.
- Separa moeda de cotação de exposição cambial.
- Regista fontes, datas, pressupostos e cobertura dos dados.
- Assinala informação insuficiente como pendente.
- Verifica cálculos com exemplos de resultado conhecido.
- Usa o Excel para comparação, verificando também as regras
  quando existirem divergências.
- Explica o que foi testado, os resultados e as limitações.
- Só declara uma funcionalidade validada com evidência.

## Documentação

- Atualiza a documentação afetada por alterações relevantes.
- README.md: objetivo, estado e instruções de utilização.
- ROADMAP.md: tarefas, prioridades e progresso.
- IDEAS.md: propostas ainda em avaliação.
- CHANGELOG.md: melhorias e correções entregues.
- Marca tarefas como concluídas apenas no âmbito correspondente:
  Excel, Python ou validação.
- Mantém estas instruções alinhadas com o projeto.

## Dados e histórico

- Usa dados fictícios nos exemplos e testes do repositório.
- Mantém dados de clientes e credenciais fora do repositório.
- Resume os ficheiros alterados e sugere uma mensagem de commit.