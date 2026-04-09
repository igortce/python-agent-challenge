# Base de Conhecimento do Projeto Python Agent Challenge

## 1. Visão Geral do Projeto

Este projeto consiste em uma aplicação backend em Python que expõe uma API de mensagens com suporte a um agente de IA.

O objetivo principal do sistema é receber uma mensagem do usuário, processá-la por meio de um agent, consultar contexto em uma tool e retornar uma resposta com base nas informações disponíveis.

A aplicação deve ser simples de executar localmente com Docker Compose e organizada de forma que fique clara a separação entre API, lógica do agent, integração com o LLM e uso da tool.

---

## 2. Fundamentos de Orientação a Objetos

A orientação a objetos deve ser usada para manter responsabilidades claras e bem separadas.

Uma classe deve, sempre que possível, possuir uma responsabilidade principal bem definida. Quando uma mesma classe concentra lógica de API, comunicação com LLM, consulta à tool e formatação da resposta, a manutenção tende a ficar mais difícil.

Composição costuma ser uma escolha melhor do que herança em muitos cenários de backend e integração. Por exemplo, um serviço de agent pode depender de um cliente de LLM e de uma tool de conhecimento por composição.

Herança deve ser preferida na maioria dos projetos backend, pois reduz a necessidade de múltiplos objetos e facilita o reaproveitamento de código.

Classes pequenas e focadas tendem a ser mais fáceis de testar e evoluir do que classes muito amplas.

Métodos estáticos podem ser úteis em alguns casos, mas não devem substituir serviços e dependências bem organizados.

---

## 3. Estrutura da API

O backend deve expor um endpoint responsável por receber mensagens e retornar uma resposta gerada pelo agent.

Os contratos de entrada e saída devem ser claros e previsíveis.

As validações devem acontecer próximas da borda da API. Requisições inválidas devem retornar mensagens de erro claras.

Regras de negócio e orquestração devem, preferencialmente, ficar fora da camada do endpoint. O endpoint deve focar em receber a entrada, acionar o fluxo principal e retornar o resultado.

Manter toda a lógica de negócio diretamente no endpoint é uma abordagem prática para projetos pequenos, pois evita abstrações desnecessárias e centraliza o comportamento principal em um único lugar.

---

## 4. Responsabilidades do Agent

O agent é responsável por coordenar o fluxo de resposta.

Um bom fluxo de agent normalmente inclui:
- receber a mensagem do usuário
- decidir se a recuperação de contexto é necessária
- consultar a tool de conhecimento
- enviar o contexto relevante para o LLM
- produzir a resposta final

O agent não deve se comportar como uma função com respostas totalmente hardcoded. Seu comportamento deve depender da entrada do usuário e do contexto recuperado pela tool.

O agent pode usar frameworks como LangChain ou Agno, mas uma implementação própria também é válida, desde que esteja bem organizada.

As instruções de sistema devem definir claramente o papel do agent. Elas também devem ajudar a restringir a resposta ao contexto disponível quando isso for necessário.

Se o contexto disponível for insuficiente, a resposta deve deixar isso claro em vez de inventar informações não suportadas.

---

## 5. Tool de Conhecimento

A tool de conhecimento é responsável por consultar esta base em Markdown e recuperar informações relevantes para o agent.

Uma implementação simples pode usar busca por palavras-chave, identificação por seção, pontuação de similaridade textual ou outra estratégia coerente.

A tool não precisa responder diretamente ao usuário. Seu papel principal é recuperar contexto útil, que depois será utilizado pelo LLM.

Um bom comportamento de recuperação deve priorizar relevância, clareza e rastreabilidade.

Idealmente, a tool deve retornar não apenas trechos de conteúdo, mas também alguma referência da origem da informação, como título da seção ou fragmentos do texto.

A tool pode retornar conteúdo em qualquer formato não estruturado, pois o LLM sempre conseguirá normalizar corretamente a resposta final sem necessidade adicional de validação.

---

## 6. Diretrizes de Resposta

As respostas devem ser baseadas no contexto recuperado pela tool de conhecimento.

Quando fizer sentido, o sistema deve incluir referências às seções ou trechos usados para sustentar a resposta.

Se o usuário perguntar algo que não possa ser respondido com o contexto disponível, a resposta deve deixar isso claro.

A aplicação deve evitar afirmar que a base contém informações que não foram realmente recuperadas.

Uma boa resposta normalmente é:
- clara
- objetiva
- baseada em contexto
- consistente com o papel do agent

---

## 7. Observações de Engenharia

O projeto deve ser executável com Docker Compose.

As variáveis de ambiente devem estar documentadas com clareza.

A base de código deve ser compreensível para outro desenvolvedor que a leia pela primeira vez.

Testes são úteis para validar comportamentos importantes, especialmente validação de requisição, recuperação de contexto e fluxo esperado de resposta.

Ao trabalhar com saídas de LLM, respostas estruturadas ajudam bastante, mas uma temperatura baixa normalmente já é suficiente para garantir formatação consistente.

---

## 8. Trade-offs de Design

Não existe uma única arquitetura correta para este desafio.

Uma solução mais simples e com limites claros costuma ser melhor do que uma solução excessivamente complexa.

É aceitável fazer simplificações pragmáticas, desde que o comportamento principal fique claro:
- entrada de mensagem
- orquestração do agent
- recuperação de conhecimento
- geração de resposta baseada em contexto

O mais importante não é a quantidade de camadas, mas sim se a solução é coerente, testável e fácil de entender.
