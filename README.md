# Sprint3_prompt_intelligencial_artificial


# ChargeGrid Intelligence - GoodWe SmartCharge Assistant

## Visão Geral do Projeto
Este projeto consiste no desenvolvimento de um assistente técnico inteligente voltado para a infraestrutura de recarga de veículos elétricos da GoodWe, com foco nos modelos comerciais GW7K, GW11K e GW22K. A solução foi projetada para auxiliar gestores de eletropostos, frotistas e operadores técnicos na resolução de dúvidas sobre controle de demanda, integração com protocolos de comunicação (OCPP), tarifação, experiência do usuário e integração fotovoltaica.

---

## Evolução e Decisões Técnicas da Sprint 03
Durante a Sprint 03, a solução passou por uma reformulação técnica completa, transitando de um modelo conversacional experimental para uma aplicação corporativa robusta baseada em agentes autônomos.

As principais implementações realizadas incluem:


### 1. Recuperação de Conhecimento em Nuvem (RAG Corporativo)
O armazenamento de vetores local anterior (baseado em ChromaDB) apresentava instabilidades de persistência e alto consumo de memória no ambiente de execução. Foi adotada a infraestrutura gerenciada de Vector Store da OpenAI (`file_search`), permitindo indexação em nuvem diretamente dos manuais técnicos oficiais e datasheets da GoodWe, o que eliminou inconsistências na recuperação dos fragmentos técnicos.

### 2. Persistência e Gerenciamento de Memória por Sessão
O histórico da aplicação deixou de ser mantido apenas de maneira volátil na memória temporária do navegador. O sistema passou a contar com persistência estruturada por sessão, garantindo continuidade de contexto, rastreabilidade e coerência conversacional através de múltiplos turnos de diálogo.

### 3. Camada Ativa de Segurança e Guardrails
Foram implementados mecanismos ativos de proteção na camada de entrada e saída do agente, garantindo:
* Bloqueio contra tentativas de injeção de prompt (Prompt Injection).
* Delimitação estrita de escopo para evitar respostas fora do domínio de mobilidade elétrica.
* Prevenção contra recomendações elétricas ou de infraestrutura que possam oferecer riscos operacionais.

### 4. Experimentação e Comparação Sistemática de Modelos
Foi conduzida uma avaliação técnica entre diferentes modelos de linguagem da OpenAI (`gpt-4o-mini` e `gpt-4o`), considerando métricas de precisão na recuperação documental (RAG), latência média de resposta e custo computacional, fundamentando a escolha do modelo ideal para o sistema.

---

## Estrutura do Repositório
* `app.py`: Código-fonte principal com a interface gráfica e o pipeline de agentes.
* `relatorio_modelos.md`: Documentação técnica contendo os testes, parâmetros e justificativa da seleção do modelo de linguagem.
* `Relatório de evolução.pdf`: Relatório analítico detalhando a comparação antes e depois, decisões de refatoração e métricas.
* `identificacao.txt`: Arquivo com a identificação acadêmica dos integrantes do projeto.
