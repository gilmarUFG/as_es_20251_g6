# 🧱 Mural: Documentação de Arquitetura de Software
**Atividade Supervisionada AS3 – Requisitos de Software**  


---

## 🎯 O que é?

> Documentação de arquitetura é o conjunto de artefatos que descrevem como um sistema está estruturado e as decisões por trás dessa estrutura.

Ela serve para:
- Comunicar a arquitetura entre equipes.
- Justificar decisões arquiteturais.
- Apoiar a manutenção e evolução do sistema.
- Ajudar novos desenvolvedores a entender o projeto.

---

## 🧠 Atores Envolvidos

- 👨‍💻 **Arquiteto de Software**
- 🧑‍💻 **Desenvolvedores**
- 📋 **Analistas de Requisitos**
- 🧑‍💼 **Usuários e Clientes**

---

## 📦 Elementos da Documentação

| Elemento                    | Descrição                                                                |
|----------------------------|--------------------------------------------------------------------------|
| 🧭 Visões Arquiteturais     | Diferentes perspectivas do sistema (lógica, física, processos, etc.)     |
| 🔄 Estilos e Padrões        | Modelos usados: MVC, camadas, microserviços, cliente-servidor, etc.      |
| 🧱 Componentes              | Módulos principais e suas funções no sistema                             |
| 🚦 Requisitos Arquiteturais | Requisitos não-funcionais (ex: desempenho, segurança, escalabilidade)    |
| 📊 Diagramas                | Representações gráficas como UML ou C4                                   |
| 📝 Decisões Arquiteturais   | Registro das decisões tomadas e suas justificativas                      |
| 🔐 Qualidades e Restrições  | Expectativas de segurança, performance, etc.                             |

---
## 📋 Requisitos de Documentação

### ✅ Requisitos de Conteúdo

| Requisito | Descrição |
|----------|-----------|
|  **Req-1: Correto** | A documentação deve ser precisa e livre de erros. Documentação incorreta pode causar mais danos do que benefícios. |
|  **Req-2: Atual** | Deve refletir fielmente as mudanças no sistema, como código, infraestrutura e interfaces. |
|  **Req-3: Compreensível** | Deve ser clara, objetiva e adaptada ao público-alvo. |
|  **Req-4: Relevante** | Estrutura, forma e conteúdo devem atender às necessidades das tarefas dos leitores. |

---

### ✍️ Requisitos Formais

| Requisito | Descrição |
|----------|-----------|
|  **Req-5: Referenciável** | Utilize um esquema de numeração consistente para títulos, diagramas e tabelas, facilitando a navegação. |
|  **Req-6: Linguagem Adequada** | Use linguagem clara, com ortografia e gramática corretas, voz ativa, afirmações positivas e frases curtas. |
|  **Req-7: Manutenível** | A documentação deve ser de fácil manutenção, permitindo que seja atualizada conforme o sistema evolui. |

---

### 🧰 Requisitos de Processos e Ferramentas

| Requisito | Descrição |
|----------|-----------|
|  **Req-8: Fácil de Encontrar** | Deve estar facilmente acessível e ser navegável e pesquisável. |
|  **Req-9: Versão Controlada** | O histórico de mudanças da documentação deve ser mantido, como fazemos com o código. |
|  **Req-10: Ferramentas Apropriadas** | As ferramentas utilizadas devem focar no conteúdo e reduzir o tempo gasto com configuração. |
|  **Req-11: Atualizado Continuamente** | A documentação deve ser constantemente revisada e expandida com cada mudança relevante. |

---

## 💡 Documentação como Código

> Ao atender aos requisitos como manutenção (Req-7), controle de versão (Req-9), uso de ferramentas (Req-10) e atualização contínua (Req-11), conclui-se que devemos tratar **documentação como código**.

### 📄 Benefícios

- Estrutura em subdocumentos;
- Organização por partes interessadas;
- Referências a imagens, sem incorporá-las diretamente;
- Documentação em formato semelhante ao código-fonte;
- Pull requests e revisões como no fluxo de desenvolvimento;
- Geração de múltiplos formatos (HTML5, PDF, Confluence, etc).
  
---

## 🛠️ Técnicas e Ferramentas

- **Modelos Visuais**: C4, UML, Diagramas de Componentes
- **Templates**: arc42, ADR (Architectural Decision Records)
- **Ferramentas**: PlantUML, Draw.io, Lucidchart

---

## 📌 Boas Práticas

- 📌 Manter sempre atualizada
- 📌 Diagramas simples e claros
- 📌 Organizar por públicos-alvo (devs, gestão, clientes)
- 📌 Relacionar requisitos e arquitetura
- 📌 Usar linguagem acessível

---

## 🧩 Exemplo de Interação entre Atores
-  Os usuários e cliente geram insumo para a definição de requisitos funcionais e de qualidade por parte do analista de requisitos.
-  Os requisitos, estruturados pelo analista, são utilizados como base na decisão de como será a arquitetura do software, definida pelo arquiteto de software.
-  A arquitetura, devidamente documentada, é usada como inspiração pelo desenvolvedor para realizar a implementação do que foi planejado.<br/>

Com base nas mudanças dos requisitos durante o projeto, esse processo pode ocorrer de forma iterativa e diversificada com o objetivo de manter a documentação sempre atualizada em relação às decisões de arquitetura.
