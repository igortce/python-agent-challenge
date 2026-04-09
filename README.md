# Python Agent Challenge

Desafio técnico para construção de um backend em Python com agente de IA, Docker Compose e fluxo de resposta com contexto.

## Objetivo

O objetivo deste desafio é avaliar a capacidade do candidato de estruturar uma aplicação backend em Python, com uso real de LLM, organização de código, integração com contexto externo e boas práticas de desenvolvimento.

A proposta é construir uma API de mensagens onde o fluxo principal seja conduzido por um agente, capaz de utilizar uma tool para consultar uma base de conhecimento em Markdown e responder com base nesse contexto.

## O que será avaliado

- Organização e clareza do código
- Estruturação da API
- Uso de Python no backend
- Uso real de LLM no fluxo principal
- Capacidade de organizar um agent simples
- Uso de tool para consulta de contexto
- Qualidade da resposta gerada
- Tratamento de erros e cenários sem resposta
- Clareza da documentação e instruções de execução

## Requisitos gerais

A solução deve conter:

- Backend em Python
- Execução via Docker Compose
- Endpoint principal de mensagens
- Uso obrigatório de LLM
- Um agent responsável pelo fluxo principal
- Pelo menos uma tool para consultar uma base de conhecimento em Markdown
- Respostas baseadas no contexto retornado pela tool

## Regras esperadas da solução

- O agent deve responder com base no contexto recuperado
- A aplicação não deve depender de respostas totalmente hardcoded
- Quando não houver informação suficiente, a solução deve lidar com isso de forma clara
- A arquitetura deve permitir entender de forma simples onde estão:
  - a API
  - a lógica do agent
  - a integração com o LLM
  - a tool de consulta ao conteúdo
- A solução deve ser simples de executar e avaliar

## Base de conhecimento

O desafio utilizará um arquivo Markdown fornecido como base de conhecimento do projeto.

Esse arquivo deverá ser consultado pela aplicação por meio de uma tool definida pelo candidato. A forma de implementação dessa consulta fica em aberto, desde que a solução demonstre organização, clareza e uso coerente do contexto recuperado.

## Entrega

A entrega deve ser feita por repositório GitHub, contendo:

- Código-fonte
- Instruções de execução
- Variáveis de ambiente necessárias
- Explicação breve da arquitetura adotada
- Explicação breve das decisões técnicas tomadas

## Observações

- O foco do desafio não é interface visual
- O foco principal está no backend, no fluxo do agent e na organização da solução
- O uso de bibliotecas e frameworks é livre, desde que a solução seja coerente com a proposta
- O candidato poderá explicar eventuais simplificações ou limitações adotadas

## Próximos detalhes

Os detalhes específicos do contrato da API, formato de entrada e saída, estrutura esperada da resposta e conteúdo do arquivo Markdown serão definidos na continuação deste documento.
