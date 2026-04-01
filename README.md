# Sistema de Gestão de Eventos — Event Management System

> **PT-BR** | [EN below](#english-version)

---

## Sobre o Projeto

Plataforma web para gestão completa de eventos com hospedagem, desenvolvida para substituir um fluxo 100% manual feito em Excel, Pipefy e Canva.

O sistema centraliza o cadastro de participantes, organização de quartos, gestão de equipes, programação de atividades e geração de relatórios — tudo em uma única interface, com controle de acesso por roles.

**Problema real resolvido:** antes deste sistema, o processo exigia exportar dados do Pipefy para Excel, organizar manualmente por idade e sexo, distribuir nos quartos, separar em equipes e gerar crachás no Canva. Com o sistema, esse fluxo inteiro é automatizado.

---

## Funcionalidades

- Dashboard com visão geral do evento (participantes, líderes, quartos, equipes)
- Cadastro e gestão de participantes com separação por sexo e faixa etária
- Gestão de líderes por quarto
- Organização de quartos (masculino, feminino)
- Gestão de equipes (masculino, feminino, mista) com controle de ocupação
- Programação de atividades
- Autenticação com controle de acesso por roles (Admin, Líder, etc.)
- Geração de relatórios exportáveis
- Geração automática de crachás de participantes e líderes
- Integração com Pipefy para importação de inscrições

> Implementado | Em desenvolvimento

---

## Stack Técnica

| Camada | Tecnologia |
|---|---|
| Backend | PHP — Laravel |
| Banco de Dados | MySQL |
| Frontend | HTML, TailwindCSS, DaisyUI, JavaScript |
| Infra | Docker, Composer |
| Testes de API | Postman |
| Versionamento | Git / GitHub |

---

## Arquitetura

```
gestao-de-eventos/
├── app/
│   ├── Http/
│   │   ├── Controllers/        # Lógica de cada módulo
│   │   └── Middleware/         # Controle de acesso por role
│   └── Models/                 # Eloquent ORM
├── database/
│   ├── migrations/             # Estrutura do banco
│   └── seeders/                # Dados de teste
├── routes/
│   └── api.php                 # Endpoints REST
├── public/
│   ├── index.html              # Dashboard
│   ├── crianças.html
│   ├── lideres.html
│   ├── quartos.html
│   ├── equipes.html
│   └── atividades.html
└── docker-compose.yml
```

---

## Como rodar localmente

### Pré-requisitos
- Docker e Docker Compose
- Composer

### Passos

```bash
# Clone o repositório
git clone https://github.com/lucasbritoeng/gestao-de-eventos.git
cd gestao-de-eventos

# Suba os containers
docker-compose up -d

# Instale as dependências PHP
composer install

# Configure o ambiente
cp .env.example .env
php artisan key:generate

# Rode as migrations
php artisan migrate --seed

# Acesse em: http://localhost:8000
```

---

## Modelo de Dados (principais entidades)

```
participants   → id, name, age, gender, room_id, team_id, role
leaders        → id, name, gender, room_id
rooms          → id, name, gender, capacity, leader_id
teams          → id, name, color, type (male/female/mixed), capacity
activities     → id, title, datetime, description, team_id
users          → id, name, email, role (admin/leader/viewer)
```

---

## Controle de Acesso por Roles

| Role | Permissões |
|---|---|
| Admin | Acesso total — cadastro, edição, relatórios |
| Líder | Visualiza seu quarto e equipe |
| Viewer | Dashboard somente leitura |

---

## Roadmap

- [x] Estrutura de frontend (HTML + Tailwind)
- [x] Dashboard com métricas do evento
- [ ] Backend Laravel com autenticação e roles
- [ ] CRUD de participantes, líderes, quartos e equipes
- [ ] Endpoints REST com validação
- [ ] Geração de relatórios PDF
- [ ] Geração de crachás automáticos
- [ ] Importação via Pipefy

---

## Autor

**Lucas Brito** — Desenvolvedor Backend PHP  
[LinkedIn](https://linkedin.com/in/lucasbritodev) · [GitHub](https://github.com/lucasbritoeng)

---

---

# English Version

## About

A web platform for complete event management with lodging, built to replace a fully manual workflow done in Excel, Pipefy, and Canva.

The system centralizes participant registration, room organization, team management, activity scheduling, and report generation — all in a single interface with role-based access control.

**Real problem solved:** before this system, the process required exporting data from Pipefy to Excel, manually organizing by age and gender, assigning rooms, splitting into teams, and generating badges in Canva. This system automates the entire flow.

---

## Features

- Dashboard with event overview (participants, leaders, rooms, teams)
- Participant registration with gender and age-based organization
- Leader management per room
- Room organization (male, female)
- Team management (male, female, mixed) with capacity tracking
- Activity scheduling
- Authentication with role-based access control (Admin, Leader, etc.)
- Exportable reports
- Automatic badge generation for participants and leaders
- Pipefy integration for registration import

> Implemented | In development

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | PHP — Laravel |
| Database | MySQL |
| Frontend | HTML, TailwindCSS, DaisyUI, JavaScript |
| Infrastructure | Docker, Composer |
| API Testing | Postman |
| Version Control | Git / GitHub |

---

## Running Locally

### Requirements
- Docker and Docker Compose
- Composer

### Steps

```bash
# Clone the repository
git clone https://github.com/lucasbritoeng/gestao-de-eventos.git
cd gestao-de-eventos

# Start containers
docker-compose up -d

# Install PHP dependencies
composer install

# Set up environment
cp .env.example .env
php artisan key:generate

# Run migrations
php artisan migrate --seed

# Access at: http://localhost:8000
```

---

## Author

**Lucas Brito** — Backend PHP Developer  
[LinkedIn](https://linkedin.com/in/lucasbritodev) · [GitHub](https://github.com/lucasbritoeng)
