Este projeto implementa um agente conversacional capaz de sugerir rotas entre pontos turísticos em Belo Horizonte, utilizando algoritmos de busca sobre um grafo real extraído do OpenStreetMap via OSMnx.

O agente foi desenvolvido usando a biblioteca `smolagents`, combinando raciocínio orientado a LLM com algoritmos clássicos de IA para encontrar caminhos no grafo urbano.

### Arquitetura do agente

A ideia principal é construir um agente que:

- Interaja com o usuário via linguagem natural;

- Converta solicitações de rota em coordenadas do grafo real da cidade;

- Busque caminhos utilizando algoritmos de busca informada e não informada, implementados no desenvolvimento do trabalho.

- Retorne respostas claras, interpretáveis e adaptadas à intenção do usuário.

Para isso, temos a ideia geral de arquitetura: o usuário sempre digita algo no prompt, conversando com o agente. Baseado na pergunta do usuário, o agente interpreta essa pergunta e executa os passos programados: 

1. Quando o prompt conté dois locais turísticos válidos: o agente extrai os nomes, mapeia para os nós mais próximos, executa BFS ou A* e retorna a rota

   <img width="707" height="493" alt="image" src="https://github.com/user-attachments/assets/308d45f2-7385-48d3-87d4-791a8e871c74" />


2. Quando a frase não se refere a um local turístico conhecido, ou não segue o padrão esperado: O agente tenta responder usando apenas o LLM. Pode retornar explicações, respostas gerais ou mensagens de erro amigáveis

   <img width="592" height="455" alt="image" src="https://github.com/user-attachments/assets/c277006b-8c57-460c-be40-aad44bc7b718" />

### Tecnologias Utilizadas

- Python 3

- smolagents – para criar o agente e treinar instruções

- OSMnx – extração e manipulação do grafo urbano

- NetworkX – operação com grafos e algoritmos

- HuggingFace Inference API / LLM – raciocínio e interpretação de comandos

### Algoritmos de Busca Implementados

- BFS – Breadth-First Search - Busca não informada
- A* – A-Star Search - Busca informada com heurística baseada em distância geográfica (haversine)

## Exemplos do agente sendo executado
Os exemplos abaixo mostram o agente sendo executado utilizando o modelo `qwen3`.
<img width="1355" height="516" alt="image" src="https://github.com/user-attachments/assets/25aa0468-0963-462c-ac92-440930211e4e" />
<img width="1085" height="644" alt="image" src="https://github.com/user-attachments/assets/9028b0b4-7554-4f93-b3dc-084f38da7f06" />
<img width="1289" height="651" alt="image" src="https://github.com/user-attachments/assets/3b1dba48-e3d6-454f-8581-f985e8c912bd" />


