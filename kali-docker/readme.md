# Kali Docker Lab

Laboratório Kali Linux utilizando Docker com persistência de dados no Windows.

## Objetivo

Criar um ambiente Kali Linux portátil e persistente para:

- estudos
- pentest
- troubleshooting
- automação
- SOC
- DevSecOps

Tecnologias utilizadas:

- Docker
- Docker Compose
- Kali Linux
- Windows
- WSL2
- GitHub

---

## Estrutura

```text
C:\labs
├── kali-docker
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── README.md
│
└── docker-data
    └── kali
```

---

## Persistência

Os arquivos ficam persistidos em:

```text
C:\labs\docker-data\kali
```

Mesmo removendo containers ou imagens Docker.

---

## Requisitos

- Windows 10/11
- Docker Desktop
- WSL2
- Git
- GitHub

---

# Configuração GitHub SSH

## Criar chave ED25519

```powershell
ssh-keygen -t ed25519 -C "SEU_EMAIL"
```

## Iniciar SSH Agent

```powershell
Get-Service ssh-agent | Set-Service -StartupType Automatic

Start-Service ssh-agent
```

## Adicionar chave

```powershell
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

## Exibir chave pública

```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
```

Adicionar no GitHub:

```text
Settings > SSH and GPG keys > New SSH key
```

## Testar SSH

```powershell
ssh -T git@github.com
```

---

# Clonar repositório

```powershell
cd C:\

git clone git@github.com:AlexNunes2/labs.git
```

---

# Configuração Git

```powershell
git config --global user.name "Alex Nunes"

git config --global user.email "SEU_EMAIL"
```

---

# Docker

## Build

```powershell
cd C:\labs\kali-docker

docker compose build
```

## Subir container

```powershell
docker compose up -d
```

## Verificar containers

```powershell
docker ps -a
```

## Entrar no Kali

```powershell
docker exec -it kali-lab bash
```

---

# Validar persistência

Dentro do container:

```bash
echo "persistencia ok" > /root/lab/teste.txt
```

No Windows:

```powershell
type C:\labs\docker-data\kali\teste.txt
```

---

# Fluxo Git

## Verificar alterações

```powershell
git status
```

## Adicionar arquivos

```powershell
git add .
```

## Commit

```powershell
git commit -m "Atualiza laboratorio Kali Docker"
```

## Push

```powershell
git push
```

## Pull

```powershell
git pull
```

---

# Docker úteis

## Logs

```powershell
docker logs kali-lab
```

## Parar container

```powershell
docker compose down
```

## Reiniciar

```powershell
docker compose up -d
```

---

# Ferramentas instaladas

- Kali Linux Headless
- Nmap
- Git
- Curl
- Wget
- Python3
- Pip
- Net-tools
- DNS Utils
- Vim
- Nano

---

# Segurança

Laboratório exclusivamente educacional.

Utilizar apenas:
- ambientes autorizados
- laboratórios
- CTFs
- redes controladas

---

# Expansões futuras

- Wazuh
- ELK
- Suricata
- DVWA
- Juice Shop
- Burp Suite
- Metasploit
- AD Lab
- SOC Lab
