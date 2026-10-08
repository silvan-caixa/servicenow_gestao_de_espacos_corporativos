CONTEXTO GERAL DO PROJETO
PROJETO: Gestão de Espaços Corporativos – Reserva de Salas

Estou desenvolvendo uma aplicação no ServiceNow para gerenciamento de espaços corporativos, inicialmente com foco em salas de reunião.

O objetivo do projeto é criar uma solução integrada para:

- cadastrar e manter a estrutura física dos espaços;
- manter o inventário de salas;
- consultar a disponibilidade das salas;
- realizar reservas;
- consultar reservas existentes;
- permitir bloqueios de salas;
- futuramente permitir expansão para outros tipos de espaços corporativos.

A aplicação será desenvolvida utilizando recursos nativos do ServiceNow, priorizando:

- App Engine Studio;
- ServiceNow Studio;
- tabelas customizadas;
- relacionamentos entre tabelas;
- referências;
- formulários;
- listas;
- UI Builder / Experiences;
- Client Scripts quando necessários;
- UI Policies quando necessários;
- Data Resources;
- ações e eventos;
- Business Rules;
- ACLs e segurança;
- automações e notificações quando necessário.

NÃO criar soluções externas em PHP, Laravel, Angular, Java ou outras tecnologias fora do ServiceNow.

==================================================
OBJETIVO DO MVP
==================================================

O MVP deve permitir que um usuário:

1. Consulte salas disponíveis.
2. Informe critérios de busca:
   - prédio;
   - andar;
   - data;
   - horário;
   - quantidade de participantes.
3. Visualize as salas que atendem aos critérios.
4. Selecione uma sala.
5. Clique em "Reservar sala".
6. Seja direcionado para o formulário de reserva.
7. O formulário deve receber automaticamente os dados da sala selecionada.
8. O usuário deve complementar/revisar os dados da reserva.
9. Salvar a reserva.
10. Consultar posteriormente suas reservas.

==================================================
MODELO CONCEITUAL
==================================================

A estrutura física será organizada aproximadamente desta forma:
```text
UNIDADE
   |
   └── PRÉDIO
          |
          └── ANDAR
                 |
                 └── SALA
```
A parte de utilização será:
```text
SALA
   |
   ├── RESERVA
   |
   └── BLOQUEIO
```
Principais entidades:

- Unidade
- Prédio
- Andar
- Sala
- Reserva
- Bloqueio

==================================================
CONCEITO DAS ENTIDADES
==================================================

UNIDADE
Representa uma unidade/localização organizacional ou física.

PRÉDIO
Representa um prédio pertencente a uma unidade.

ANDAR
Representa um andar pertencente a um prédio.

SALA
Representa uma sala física disponível para utilização.

A sala deverá possuir informações como:
- nome/número da sala;
- prédio;
- andar;
- capacidade;
- endereço, quando aplicável;
- situação/status;
- outras características que sejam necessárias ao MVP.

RESERVA
Representa a utilização programada de uma sala.

Deve possuir informações como:
- sala;
- solicitante;
- data;
- horário inicial;
- horário final;
- quantidade de participantes;
- finalidade/assunto;
- status;
- observações.

BLOQUEIO
Representa um período em que uma sala não pode ser reservada.

Deve possuir informações como:
- sala;
- data inicial;
- data final;
- horário inicial;
- horário final;
- motivo;
- status;
- observações.

==================================================
PRINCÍPIOS DE IMPLEMENTAÇÃO
==================================================

1. Utilizar recursos nativos do ServiceNow sempre que possível.

2. Utilizar campos Reference para relacionamentos entre entidades.

3. Evitar duplicação de dados.

4. Utilizar nomes técnicos consistentes.

5. Manter separação clara entre:
   - modelo de dados;
   - interface;
   - regras de negócio;
   - segurança;
   - automações.

6. Não implementar regras de negócio complexas antes da etapa definida para elas.

7. Não criar funcionalidades que não tenham sido solicitadas no STEP atual.

8. Não modificar funcionalidades já implementadas sem necessidade.

9. Antes de criar uma tabela, campo, página ou componente, verificar se ele já existe.

10. Evitar criar registros duplicados.

11. Sempre respeitar o Application Scope da aplicação atual.

12. A implementação deve ser incremental.

==================================================
REGRAS DE NEGÓCIO DO MVP
==================================================

As regras de negócio serão implementadas em etapas posteriores.

Entre as regras previstas estão:

- uma sala não deve possuir duas reservas conflitantes;
- uma sala deve possuir capacidade compatível com a quantidade de participantes;
- sala inativa não deve ser reservável;
- sala bloqueada não deve estar disponível;
- reservas devem possuir data e horário válidos;
- uma reserva deve estar vinculada a uma sala;
- uma reserva deve possuir solicitante;
- horários inicial e final devem ser coerentes.

IMPORTANTE:

NÃO implementar essas regras automaticamente agora.

Cada regra será tratada no STEP específico correspondente.

==================================================
INTERFACE
==================================================

A experiência principal do usuário deverá possuir uma interface simples e intuitiva.

Fluxo principal:

CONSULTAR DISPONIBILIDADE
        ↓
INFORMAR FILTROS
        ↓
LISTAR SALAS DISPONÍVEIS
        ↓
SELECIONAR SALA
        ↓
RESERVAR SALA
        ↓
FORMULÁRIO DE RESERVA
        ↓
SALVAR RESERVA

A consulta de disponibilidade deverá utilizar uma Experience/UI Builder.

==================================================
ESTRATÉGIA DE DESENVOLVIMENTO
==================================================

O projeto será implementado em STEPs.

Cada STEP possui um objetivo específico.

A IA deve:

- executar somente o STEP solicitado;
- não antecipar funcionalidades de STEPs posteriores;
- informar quais elementos foram criados;
- informar nomes técnicos;
- informar dependências;
- identificar problemas antes de alterar elementos existentes;
- evitar duplicações;
- respeitar o modelo conceitual definido neste contexto.

Quando houver ambiguidade, priorizar a solução nativa do ServiceNow e explicar a decisão.

Não alterar a arquitetura geral sem justificar.

Este contexto deve ser considerado como a referência arquitetural do projeto durante toda a implementação.
