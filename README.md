# 🚀 n8n + Redis Workflow Orchestrator

Este repositório contém uma configuração completa para executar o [n8n](https://n8n.io/) com suporte ao Redis usando Docker Compose. Ideal para automações robustas, persistência de dados e escalabilidade.

## 📦 Estrutura do Projeto

- **n8n**: Plataforma de automação baseada em fluxo.
- **Redis**: Usado para armazenar o `update_id` e outros dados temporários.
- **Docker Compose**: Orquestra os serviços de forma simples e eficiente.

## 🛠️ Pré-requisitos

- Docker instalado ([Guia oficial](https://docs.docker.com/get-docker/))
- Docker Compose instalado ([Guia oficial](https://docs.docker.com/compose/install/))

## 📁 Arquivos principais

```bash
.
├── docker-compose.yml
├── README.md
└── .env
```

## ⚙️ Como iniciar
- Clone o repositório:
``` bash
git clone https://github.com/seu-usuario/n8n-redis-workflow.git
cd n8n-redis-workflow
```

- Configure as variáveis de ambiente no arquivo .env
```env
N8N_PORT=5678
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=admin123
REDIS_PORT=6379
```

- Inicie os serviços:
```bash
docker-compose up -d
```

- Acesse o n8n em: http://localhost:5678

## 🧠 Fluxo de trabalho
O fluxo implementado realiza:
- Long polling no bot do Telegram
- Identificação de mensagens de texto e áudio
- Transcrição de áudios via Google Gemini
- Armazenamento do update_id no Redis
- Encaminhamento para subworkflow de resposta

## 🖼️ Capturas de tela
Interface do fluxo no n8n
Fluxo principal
Detalhes da automação com Redis e Gemini
Detalhes do fluxo
![Outra descrição](./Captura%20de%20tela%202025-08-22%20095351.png)
![Descrição da imagem](./Captura%20de%20tela%202025-08-22%20095059.png)


## 🧪 Testes e validação
Para testar o fluxo:
- Envie uma mensagem ou áudio para o bot do Telegram
- Verifique se o conteúdo é transcrito e armazenado corretamente
- Acompanhe os logs com:
```bash
docker-compose logs -f
```


## 📌 Observações
- Certifique-se de configurar corretamente as credenciais do Telegram e Google Gemini no n8n.
- O Redis é usado como cache para evitar reprocessamento de mensagens.
