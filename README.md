# ConcursoMap / EditalMatch

> **Plataforma web para agregação, normalização e recomendação personalizada de concursos públicos com base no perfil do candidato.**

## 👥 Grupo

**4Minds**

### Integrantes

* Davi Robson
* Paloma Silva
* Daniela Marques
* Isabela Jorge

---

## 📌 Sobre o projeto

O **ConcursoMap / EditalMatch** é uma plataforma web desenvolvida com o objetivo de facilitar a descoberta e o acompanhamento de concursos públicos.

A proposta consiste em reunir informações provenientes de diferentes fontes, **normalizar os dados dos concursos** e apresentar oportunidades de forma personalizada, considerando as características e preferências cadastradas pelo candidato.

Em vez de apenas disponibilizar uma lista de concursos, a plataforma busca responder a uma pergunta mais relevante para o usuário:

> **"Quais concursos são mais compatíveis com o meu perfil?"**

O sistema também pretende auxiliar o candidato no acompanhamento de oportunidades, prazos e alterações relevantes nos concursos cadastrados.

---

## 🎯 Objetivo

Desenvolver uma plataforma web capaz de:

* Agregar informações de concursos públicos provenientes de diferentes fontes;
* Normalizar informações apresentadas em diferentes formatos;
* Permitir a pesquisa e filtragem de concursos;
* Cadastrar e gerenciar o perfil do candidato;
* Identificar oportunidades compatíveis com o perfil do usuário;
* Apresentar um índice de compatibilidade;
* Explicar os fatores que contribuíram para a recomendação;
* Permitir o acompanhamento de concursos favoritos;
* Monitorar prazos importantes;
* Registrar alterações relevantes nos concursos;
* Disponibilizar as fontes das informações apresentadas.

---

## 💡 Problema

Candidatos a concursos públicos precisam consultar diferentes sites, órgãos, bancas examinadoras e editais para encontrar oportunidades compatíveis com sua formação, localização, área de interesse e expectativas profissionais.

Além da dispersão das informações, os concursos podem apresentar diferentes estruturas, nomenclaturas e formatos de divulgação.

Essa situação dificulta:

* Encontrar oportunidades relevantes;
* Comparar diferentes concursos;
* Identificar requisitos;
* Acompanhar prazos;
* Perceber alterações em editais;
* Avaliar rapidamente se determinado concurso é adequado ao perfil do candidato.

O **ConcursoMap / EditalMatch** propõe centralizar e organizar essas informações, adicionando uma camada de recomendação personalizada.

---

## 🚀 Proposta de solução

A plataforma será organizada em quatro etapas principais:

```text
Fontes de dados
      ↓
Coleta
      ↓
Normalização
      ↓
Banco de concursos
      ↓
Perfil do candidato
      ↓
Motor de compatibilidade
      ↓
Recomendações personalizadas
      ↓
Acompanhamento e notificações
```

O candidato poderá informar características como:

* Escolaridade;
* Formação;
* Área de interesse;
* Localização;
* Faixa salarial desejada;
* Preferências relacionadas aos concursos.

A partir dessas informações, o sistema poderá apresentar oportunidades com diferentes níveis de compatibilidade.

### Exemplo

```text
Analista de Tecnologia da Informação
Órgão X

Compatibilidade: 94%

✓ Escolaridade compatível
✓ Formação compatível
✓ Área de interesse compatível
✓ Localização compatível
✓ Remuneração compatível
```

O objetivo é que a recomendação seja **explicável**, permitindo que o candidato entenda por que determinada oportunidade foi considerada compatível.

---

## 🧩 Principais funcionalidades

### 👤 Perfil do candidato

* Cadastro de usuário;
* Autenticação;
* Cadastro de escolaridade;
* Formação acadêmica;
* Áreas de interesse;
* Localização;
* Pretensão salarial;
* Preferências.

### 🔎 Pesquisa de concursos

* Pesquisa por palavra-chave;
* Filtro por área;
* Filtro por localização;
* Filtro por escolaridade;
* Filtro por remuneração;
* Filtro por situação do concurso;
* Filtro por período de inscrição.

### 🎯 Recomendação personalizada

* Cálculo de compatibilidade;
* Ranking de concursos;
* Justificativa da recomendação;
* Identificação dos critérios atendidos e não atendidos.

### ⭐ Favoritos

* Adicionar concursos aos favoritos;
* Remover concursos dos favoritos;
* Visualizar concursos acompanhados.

### 📅 Acompanhamento

* Datas de inscrição;
* Data de prova;
* Prazo de inscrição;
* Alterações no cronograma;
* Histórico de alterações.

### 🔔 Notificações

Possibilidade de alertar o candidato sobre:

* Aproximação do fim das inscrições;
* Alterações no concurso;
* Novos concursos compatíveis;
* Atualizações importantes.

### 📄 Editais

* Disponibilização da fonte oficial;
* Processamento de informações do edital;
* Extração de informações estruturadas;
* Registro da origem dos dados.

### 🛠️ Área administrativa

* Cadastro e edição de concursos;
* Validação de informações coletadas;
* Gerenciamento das fontes;
* Correção de dados;
* Visualização de falhas de coleta;
* Histórico de alterações.

---

## 🏗️ Arquitetura

A aplicação será desenvolvida utilizando uma arquitetura web baseada em **frontend, API backend, banco de dados e serviços de processamento de dados**.

```text
                         ┌─────────────────┐
                         │     Usuário     │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ React + Vite    │
                         │   Front-end     │
                         └────────┬────────┘
                                  │
                               REST API
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Node.js         │
                         │ Express         │
                         └────────┬────────┘
                                  │
                    ┌─────────────┼─────────────┐
                    ▼             ▼             ▼
              ┌──────────┐ ┌───────────┐ ┌────────────┐
              │PostgreSQL│ │   Match   │ │Notificações│
              │          │ │   Engine  │ │            │
              └──────────┘ └───────────┘ └────────────┘
                    ▲
                    │
             ┌──────┴───────┐
             │              │
       ┌────────────┐ ┌────────────┐
       │  Scraping  │ │   Editais  │
       │ Playwright │ │     PDF    │
       └─────┬──────┘ └─────┬──────┘
             │              │
             └──────┬───────┘
                    ▼
              ┌────────────┐
              │Normalização│
              │  de dados  │
              └────────────┘
```

---

## 🛠️ Tecnologias

### Front-end

* **React**
* **Vite**
* **JavaScript / TypeScript**
* **HTML5**
* **CSS3**

### Back-end

* **Node.js**
* **Express**

### Banco de dados

* **PostgreSQL**
* **Prisma ORM**

### Coleta e processamento

* **Playwright**
* Processamento de documentos PDF
* API de inteligência artificial para extração estruturada de informações

### Autenticação

* **JWT**
* **bcrypt**

### Testes

* **Vitest**
* **Supertest**
* **Playwright**

### Versionamento e infraestrutura

* **Git**
* **GitHub**
* **Docker**
* **Azure**

---

## 🗃️ Modelo conceitual

Entre as principais entidades previstas estão:

```text
Usuário
 ├── Perfil
 ├── Preferências
 ├── Favoritos
 └── Notificações

Concurso
 ├── Órgão
 ├── Banca
 ├── Cargo
 ├── Requisitos
 ├── Vagas
 ├── Cronograma
 ├── Edital
 ├── Fonte
 └── Histórico

Usuário
      │
      ▼
Compatibilidade
      │
      ▼
Concurso
```

---

## 🤖 Uso de inteligência artificial

A inteligência artificial será utilizada como recurso auxiliar no processamento dos editais.

Um possível fluxo é:

```text
Edital PDF
    ↓
Extração do texto
    ↓
Processamento por IA
    ↓
Informações estruturadas
    ↓
Validação
    ↓
Banco de dados
```

A IA poderá auxiliar na identificação de informações como:

* Cargo;
* Número de vagas;
* Escolaridade;
* Remuneração;
* Requisitos;
* Datas de inscrição;
* Data da prova;
* Etapas;
* Banca organizadora.

A IA não deverá ser considerada a fonte oficial das informações. Sempre que possível, os dados serão associados à **fonte original do concurso**, permitindo sua conferência.

---

## 🎯 Motor de compatibilidade

O sistema utilizará critérios definidos para comparar o perfil do candidato com os requisitos de cada oportunidade.

Exemplo de critérios:

| Critério          |     Peso |
| ----------------- | -------: |
| Escolaridade      |      25% |
| Formação          |      25% |
| Área de interesse |      20% |
| Localização       |      15% |
| Remuneração       |      10% |
| Preferências      |       5% |
| **Total**         | **100%** |

O resultado poderá ser apresentado como um percentual de compatibilidade.

> Os pesos acima representam uma proposta inicial e poderão ser ajustados durante o desenvolvimento e validação do projeto.

---

## 🔐 Segurança e privacidade

A plataforma deverá considerar princípios de segurança e proteção de dados, evitando o armazenamento de informações pessoais desnecessárias para o funcionamento do sistema.

Entre as medidas previstas estão:

* Autenticação segura;
* Senhas armazenadas utilizando hash;
* Controle de acesso;
* Proteção das rotas da API;
* Validação dos dados recebidos;
* Minimização de dados pessoais;
* Registro de ações administrativas;
* Utilização de fontes oficiais para conferência das informações.

---

## 📊 Qualidade dos dados

A confiabilidade das informações é um dos principais aspectos do projeto.

Para isso, cada informação poderá estar associada a:

* Fonte;
* URL da fonte;
* Data da coleta;
* Data da última verificação;
* Histórico de alterações;
* Status de validação.

O sistema deverá deixar claro que as informações possuem caráter informativo e que o candidato deve consultar o edital e a fonte oficial antes de realizar sua inscrição.

---

## 📋 Escopo inicial

Para manter o projeto viável, o MVP será concentrado nas funcionalidades essenciais:

* [ ] Cadastro e autenticação;
* [ ] Perfil do candidato;
* [ ] Cadastro de concursos;
* [ ] Banco de dados relacional;
* [ ] Pesquisa e filtros;
* [ ] Página de detalhes do concurso;
* [ ] Favoritos;
* [ ] Motor de compatibilidade;
* [ ] Recomendações personalizadas;
* [ ] Fonte oficial das informações;
* [ ] Acompanhamento de prazos;
* [ ] Coleta automatizada de dados;
* [ ] Histórico de alterações;
* [ ] Painel administrativo.

Funcionalidades como aplicativo mobile completo, marketplace, sistema de questões, videoaulas e funcionalidades avançadas de IA poderão ser consideradas como **evoluções futuras**, não fazendo parte do núcleo inicial do projeto.

---

## 🗺️ Roadmap

### Fase 1 — Planejamento

* [ ] Levantamento de requisitos;
* [ ] Definição do escopo;
* [ ] Casos de uso;
* [ ] Modelagem do banco;
* [ ] Protótipos das telas.

### Fase 2 — Desenvolvimento da base

* [ ] Configuração do projeto;
* [ ] Backend;
* [ ] Frontend;
* [ ] Banco de dados;
* [ ] Autenticação.

### Fase 3 — Concursos

* [ ] Cadastro;
* [ ] Listagem;
* [ ] Busca;
* [ ] Filtros;
* [ ] Detalhes;
* [ ] Favoritos.

### Fase 4 — Recomendação

* [ ] Perfil do candidato;
* [ ] Regras de compatibilidade;
* [ ] Cálculo do índice;
* [ ] Ranking;
* [ ] Explicação da recomendação.

### Fase 5 — Automação

* [ ] Coleta de fontes;
* [ ] Normalização;
* [ ] Processamento de PDFs;
* [ ] Atualização automática;
* [ ] Histórico.

### Fase 6 — Notificações

* [ ] Alertas de prazo;
* [ ] Alertas de alterações;
* [ ] Novos concursos compatíveis.

### Fase 7 — Testes e implantação

* [ ] Testes unitários;
* [ ] Testes de integração;
* [ ] Testes End-to-End;
* [ ] Dockerização;
* [ ] CI/CD;
* [ ] Deploy no Azure.

---

## 📁 Estrutura prevista do repositório

```text
concurso-map/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── hooks/
│   │   └── utils/
│   └── package.json
│
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── repositories/
│   │   ├── middlewares/
│   │   ├── collectors/
│   │   ├── parsers/
│   │   └── jobs/
│   └── package.json
│
├── database/
│   ├── migrations/
│   └── seed/
│
├── docs/
│
├── tests/
│
├── docker-compose.yml
├── README.md
└── .gitignore
```

---

## 👥 Equipe — 4Minds

| Integrante          | Participação               |
| ------------------- | -------------------------- |
| **Davi Robson**     | Desenvolvimento do projeto |
| **Paloma Silva**    | Desenvolvimento do projeto |
| **Daniela Marques** | Desenvolvimento do projeto |
| **Isabela Jorge**   | Desenvolvimento do projeto |

As responsabilidades individuais poderão ser definidas e documentadas conforme a divisão das atividades do projeto.

---

## 🎓 Contexto acadêmico

Este projeto é desenvolvido no contexto acadêmico do grupo **4Minds**, tendo como tema:

> **Desenvolvimento de uma Plataforma web para agregação, normalização e recomendação personalizada de concursos públicos com base no perfil do candidato.**

O projeto busca aplicar conhecimentos de desenvolvimento web, banco de dados, engenharia de software, processamento de dados, automação e inteligência artificial na construção de uma solução voltada ao acompanhamento de concursos públicos.

---

## ⚠️ Observação

O **ConcursoMap / EditalMatch** não substitui o edital oficial ou os canais oficiais dos órgãos e bancas organizadoras.

As informações disponibilizadas pela plataforma deverão ser utilizadas como apoio à pesquisa, sendo responsabilidade do candidato consultar a **fonte oficial** antes de tomar decisões relacionadas à inscrição ou participação em concursos.

---

## 📄 Licença

A licença do projeto será definida posteriormente pelo grupo **4Minds**.
