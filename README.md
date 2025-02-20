# 🛡️ Aegis AI Security | CamIASecurity 2.0

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Python](https://img.shields.io/badge/Python-3.8%2B-brightgreen)
![Django](https://img.shields.io/badge/Django-4.1-green)
![React](https://img.shields.io/badge/React-18.0-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10-orange)

**Vigilância Inteligente, Proteção Constante**

## 📋 Visão Geral

O Aegis AI Security é um sistema de segurança inteligente que utiliza inteligência artificial para analisar streams de vídeo em tempo real, detectar comportamentos suspeitos e emitir alertas automáticos. Nosso objetivo é revolucionar a maneira como a segurança é gerenciada, reduzindo dependência de monitoramento humano constante e aumentando a eficácia da detecção de incidentes.

![Dashboard Preview](https://via.placeholder.com/800x400?text=Aegis+AI+Security+Dashboard)

## 🚀 Principais Funcionalidades

- **Detecção Automática de Comportamentos**:
  - Brigas e agressões
  - Pessoas caídas
  - Aglomerações suspeitas
  - Movimentação em áreas restritas

- **Zonas de Alerta Personalizáveis**:
  - Definição de perímetros virtuais
  - Alertas por tipo de incidente
  - Programação por horário

- **Analytics Avançado**:
  - Heatmaps de movimento
  - Contagem de pessoas
  - Tempo médio de permanência
  - Relatórios customizáveis

- **Sistema de Notificação**:
  - Alertas em tempo real
  - Notificações por email/SMS
  - Categorização por severidade
  - Confirmação de visualização

## 🔧 Arquitetura (DDD Adaptado ao Django)

```
aegis-ai-security/
├── backend/                               # Backend Django com DRF
│   ├── aegis_project/                     # Configuração do projeto
│   │   ├── settings/                      # Configurações por ambiente
│   │   ├── urls.py                        # Rotas principais
│   │   └── asgi.py                        # Configuração ASGI p/ websockets
│   │
│   ├── core/                              # Domínio Core (Shared Kernel)
│   │   ├── domain/                        # Conceitos compartilhados
│   │   │   ├── value_objects/             # Objetos de valor
│   │   │   └── events/                    # Eventos de domínio 
│   │
│   ├── security/                          # Bounded Context: Segurança
│   │   ├── domain/                        # Camada de Domínio
│   │   │   ├── models/                    # Entidades e agregados
│   │   │   ├── repositories/              # Interfaces de repositório 
│   │   │   ├── services/                  # Serviços de domínio
│   │   │   └── events/                    # Eventos específicos
│   │   │
│   │   ├── application/                   # Camada de Aplicação
│   │   │   ├── dtos/                      # Objetos de transferência
│   │   │   ├── use_cases/                 # Casos de uso
│   │   │   └── commands/                  # Comandos
│   │   │
│   │   ├── infrastructure/                # Camada de Infraestrutura
│   │   │   ├── repositories/              # Implementações de repositório
│   │   │   ├── serializers/               # Serializers do DRF
│   │   │   └── adapters/                  # Adaptadores externos
│   │   │
│   │   └── interfaces/                    # Camada de Interface
│   │       ├── api/                       # APIs REST (ViewSets)
│   │       ├── consumers/                 # Websocket consumers
│   │       └── tasks/                     # Tarefas Celery
│   │
│   ├── analytics/                         # Bounded Context: Analytics
│   │   ├── domain/                        # (estrutura similar)
│   │   ├── application/                   # (estrutura similar)
│   │   ├── infrastructure/                # (estrutura similar)
│   │   └── interfaces/                    # (estrutura similar)
│   │
│   ├── detection/                         # Bounded Context: Detecção ML
│   │   ├── domain/                        # (estrutura similar)
│   │   ├── application/                   # (estrutura similar)
│   │   ├── infrastructure/                # (estrutura similar)
│   │   │   ├── ml_engine/                 # Motor de ML
│   │   │   │   ├── behavior_detection/    # Detecção de comportamentos
│   │   │   │   ├── motion_tracking/       # Rastreamento de movimento
│   │   │   │   └── zone_monitoring/       # Monitoramento de zonas
│   │   └── interfaces/                    # (estrutura similar)
│   │
│   └── notifications/                     # Bounded Context: Notificações
│       └── (estrutura similar)
│
├── frontend/                              # Frontend React
│   ├── src/
│   │   ├── components/                    # Componentes reutilizáveis
│   │   ├── pages/                         # Páginas da aplicação
│   │   ├── contexts/                      # Context API
│   │   └── services/                      # Serviços e APIs
├── ml_models/                             # Modelos treinados
│   ├── behavior_classifier/               # Classificador de comportamentos
│   └── object_detector/                   # Detector de objetos
└── docker/                                # Configuração Docker
```

## 🔍 Fluxo de Funcionamento (Seguindo DDD)

1. **Camada de Interface**:
   - Câmeras enviam streams de vídeo através de adaptadores de entrada
   - Controllers recebem os dados e encaminham para os casos de uso

2. **Camada de Aplicação**:
   - Casos de uso coordenam o fluxo da aplicação
   - Comandos e consultas são processados
   
3. **Camada de Domínio**:
   - Serviços de domínio processam streams de vídeo
   - Comportamentos e objetos são detectados e classificados
   - Eventos de domínio são disparados ao detectar incidentes
   - Regras de negócio são aplicadas para verificação de alertas

4. **Camada de Infraestrutura**:
   - Motor ML processa frames de vídeo
   - Repositórios persistem incidentes e configurações
   - Adaptadores de notificação enviam alertas
   - Event bus distribui eventos para outros bounded contexts

## 🛠️ Tecnologias e Padrões Utilizados

### Backend
- **Django**: Framework web
- **Django REST Framework (DRF)**: APIs RESTful
- **Domain-Driven Design (DDD)**: Arquitetura adaptada ao Django
- **Celery**: Processamento assíncrono
- **Redis**: Cache e filas de mensagens
- **PostgreSQL**: Banco de dados principal
- **Django Channels**: WebSockets para comunicação em tempo real

### Frontend
- **React**: Biblioteca UI
- **TailwindCSS**: Framework CSS
- **Redux**: Gerenciamento de estado
- **Socket.io**: Comunicação em tempo real

### IA/ML
- **TensorFlow/Keras**: Treinamento de modelos
- **OpenCV**: Processamento de imagem
- **YOLOv5**: Detecção de objetos
- **MediaPipe**: Pose estimation

### DevOps
- **Docker**: Containerização
- **Nginx**: Servidor web/proxy
- **GitHub Actions**: CI/CD
- **Prometheus/Grafana**: Monitoramento

## ⚙️ Instalação e Configuração

### Pré-requisitos
- Python 3.8+
- Node.js 14+
- Docker e Docker Compose
- CUDA compatível (para aceleração GPU)
- Conhecimento de DDD e padrões de arquitetura limpa

### Configuração de Desenvolvimento

1. Clone o repositório:
```bash
git clone https://github.com/aegis-ai/security-system.git
cd security-system
```

2. Configure o ambiente virtual Python:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate  # Windows
pip install -r requirements.txt
```

3. Configure o frontend:
```bash
cd frontend
npm install
```

4. Configure as variáveis de ambiente:
```bash
cp .env.example .env
# Edite o arquivo .env com suas configurações
```

5. Inicie o servidor de desenvolvimento:
```bash
# Backend
cd backend
python manage.py migrate
python manage.py runserver

# Frontend
cd frontend
npm start
```

### Usando Docker

```bash
docker-compose up -d
```

## 🧪 Testes

```bash
# Testes do backend
cd backend
pytest

# Testes do frontend
cd frontend
npm test
```

## 📊 Roadmap

### Fase 1: MVP (1-2 meses)
- [x] Implementação básica do backend
- [x] Interface de usuário mínima
- [x] Integração com câmeras RTSP/ONVIF
- [x] Detecção básica de pessoas

### Fase 2: Aprimoramento (2-3 meses)
- [ ] Detecção de comportamentos específicos
- [ ] Sistema de zonas configuráveis
- [ ] Análise de fluxo básica
- [ ] Notificações em tempo real

### Fase 3: Refinamento (4-6 meses)
- [ ] Dashboard analítico avançado
- [ ] Sistema de busca por características
- [ ] Integração com sistemas de controle de acesso
- [ ] Aplicativo mobile para notificações

## 👥 Equipe

- **João Silva** - Desenvolvedor Full Stack / Líder Técnico
- **Maria Oliveira** - Especialista em ML/IA
- **Carlos Santos** - Desenvolvedor Frontend
- **Ana Pereira** - Desenvolvedora Backend

## 📄 Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 📧 Contato

Para suporte técnico ou colaborações:  
Email: contato@aegis-ai-security.com.br

---

<p align="center">Desenvolvido com ❤️ pela Equipe Aegis AI</p>