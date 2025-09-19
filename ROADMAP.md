# 🗺️ Roadmap de Estudos DevOps

Este roadmap foi criado para guiar os estudos em DevOps de forma lógica e progressiva, desde os conceitos fundamentais até as ferramentas mais avançadas. Use os checkboxes para acompanhar sua jornada de aprendizado.

---

## Módulo 1: Fundamentos Essenciais

A base para qualquer profissional de DevOps.

- [ ] **Sistemas Operacionais e Linux**
  - [ ] Navegação e manipulação de arquivos/diretórios (`ls`, `cd`, `cp`, `mv`, `rm`, `mkdir`)
  - [ ] Gerenciamento de permissões (`chmod`, `chown`)
  - [ ] Processos (`ps`, `kill`, `top`)
  - [ ] Redes (`ping`, `netstat`, `curl`, `wget`)
  - [ ] Shell Scripting básico (Bash)

- [ ] **Redes de Computadores**
  - [ ] Modelo TCP/IP e OSI
  - [ ] Entender o que é um Endereço IP, Máscara de Sub-rede e Gateway
  - [ ] Protocolos essenciais: HTTP, HTTPS, SSH
  - [ ] DNS: O que é e como funciona
  - [ ] Conceitos de Firewall e Portas

- [ ] **Controle de Versão com Git**
  - [ ] Comandos básicos (`init`, `clone`, `add`, `commit`, `push`, `pull`)
  - [ ] Estratégias de Branching (Git Flow, GitHub Flow)
  - [ ] Merging e Rebase
  - [ ] Pull Requests (Code Review)
  - [ ] Lidar com conflitos

---

## Módulo 2: Conteinerização e Orquestração

Empacotando e gerenciando aplicações de forma isolada e escalável.

- [ ] **Docker**
  - [ ] Entender a diferença: Contêineres vs. Máquinas Virtuais
  - [ ] Escrever um `Dockerfile`
  - [ ] Ciclo de vida de Imagens (`build`, `pull`, `push`, `rmi`)
  - [ ] Ciclo de vida de Contêineres (`run`, `ps`, `stop`, `rm`, `logs`, `exec`)
  - [ ] Persistência de dados com Volumes
  - [ ] Redes em Docker (`bridge`, `host`, `overlay`)
  - [ ] Orquestração local com `docker-compose`

- [ ] **Kubernetes (K8s)**
  - [ ] Arquitetura (Control Plane, Nodes, etcd)
  - [ ] `kubectl`: A ferramenta de linha de comando
  - [ ] Objetos principais:
    - [ ] `Pod`
    - [ ] `ReplicaSet` & `Deployment`
    - [ ] `Service` (ClusterIP, NodePort, LoadBalancer)
    - [ ] `Namespace`
  - [ ] Gerenciamento de Configuração: `ConfigMap` e `Secret`
  - [ ] Armazenamento: `PersistentVolume` e `PersistentVolumeClaim`
  - [ ] Gerenciador de pacotes: `Helm`

---

## Módulo 3: CI/CD - Integração e Entrega Contínua

Automatizando o ciclo de vida do desenvolvimento de software.

- [ ] **Conceitos de CI/CD**
  - [ ] O que é Integração Contínua (CI)?
  - [ ] O que é Entrega Contínua (CD)?
  - [ ] O que é Implantação Contínua (Continuous Deployment)?
  - [ ] Entender o que é um Pipeline

- [ ] **Ferramentas de CI/CD**
  - [ ] **GitHub Actions:**
    - [ ] Sintaxe de Workflows (YAML)
    - [ ] Eventos, Jobs e Steps
    - [ ] Uso de Actions da comunidade
    - [ ] Gerenciamento de Segredos
  - [ ] (Opcional) Jenkins: Entender o conceito de Jenkinsfile
  - [ ] (Opcional) GitLab CI: Entender o `.gitlab-ci.yml`

- [ ] **Gerenciamento de Artefatos**
  - [ ] O que é um repositório de artefatos?
  - [ ] Exemplos: Nexus, Artifactory, GitHub Packages

---

## Módulo 4: Infraestrutura como Código (IaC)

Gerenciando e provisionando infraestrutura através de código.

- [ ] **Conceitos de IaC**
  - [ ] Abordagem Declarativa vs. Imperativa
  - [ ] Idempotência

- [ ] **Terraform**
  - [ ] Sintaxe HCL (HashiCorp Configuration Language)
  - [ ] Providers (AWS, Azure, GCP)
  - [ ] Recursos, Variáveis e Outputs
  - [ ] Gerenciamento de Estado (`terraform.tfstate`)
  - [ ] Módulos para reutilização de código

- [ ] **Gerenciamento de Configuração com Ansible**
  - [ ] O que é e por que usar (vs. Terraform)
  - [ ] Escrever Playbooks
  - [ ] Inventário (Inventory)
  - [ ] Roles para organização

---

## Módulo 5: Cloud, Monitoramento e Observabilidade

Operando e garantindo a saúde das aplicações em produção.

- [ ] **Provedores de Cloud (Escolha um para focar)**
  - [ ] Conceitos: IaaS, PaaS, SaaS
  - [ ] **AWS:** EC2, S3, VPC, IAM, RDS
  - [ ] **Azure:** Virtual Machines, Blob Storage, VNet, Azure AD, Azure SQL
  - [ ] **GCP:** Compute Engine, Cloud Storage, VPC, IAM, Cloud SQL

- [ ] **Monitoramento e Observabilidade**
  - [ ] Os 3 Pilares: Logs, Métricas e Traces
  - [ ] **Métricas:** Prometheus
  - [ ] **Logs:** Stack ELK (Elasticsearch, Logstash, Kibana) ou Grafana Loki
  - [ ] **Visualização:** Grafana para criar dashboards

---

## Módulo 6: Tópicos Avançados e Cultura

Aperfeiçoando o processo e a segurança.

- [ ] **Segurança (DevSecOps)**
  - [ ] SAST (Static Application Security Testing)
  - [ ] DAST (Dynamic Application Security Testing)
  - [ ] Análise de vulnerabilidades em dependências
  - [ ] Análise de segurança em imagens de contêineres (ex: Trivy)

- [ ] **Service Mesh**
  - [ ] O que é e quais problemas resolve?
  - [ ] Exemplos: Istio, Linkerd

- [ ] **GitOps**
  - [ ] O que é e como funciona?
  - [ ] Ferramentas: ArgoCD, Flux

- [ ] **Cultura DevOps**
  - [ ] Os pilares: CAMS (Culture, Automation, Measurement, Sharing)
  - [ ] Práticas de colaboração e comunicação