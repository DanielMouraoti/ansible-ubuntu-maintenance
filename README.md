# Automação de Gestão de Patches Ubuntu com Ansible

Este projeto nasceu de uma necessidade real de infraestrutura: otimizar a atualização de segurança de mais de 60 estações de trabalho Ubuntu. A solução utiliza **Ansible** para garantir que todas as máquinas estejam em conformidade, eliminando falhas de segurança reportadas em dashboards de monitoramento.

## Cenário e Motivação
Através do monitoramento via **Grafana/Zabbix**, identifiquei um volume crítico de pacotes pendentes de atualização no parque tecnológico. A execução manual host-a-host era inviável. 

**Objetivo:** Criar uma estrutura de **Infrastructure as Code (IaC)** capaz de realizar o ciclo completo de manutenção (Update, Upgrade, Dist-Upgrade e Autoremove) de forma simultânea e segura.

## Tecnologias e Conceitos
- **Ansible:** Arquitetura *agentless* para automação.
- **SSH (ED25519):** Comunicação segura entre a estação de controle e os hosts.
- **IaC (Infrastructure as Code):** Padronização de ambientes via código.
- **Observability-Driven Automation:** Automação baseada em dados de monitoramento.

## Estrutura do Projeto
- `inventory/`: Gerenciamento de hosts e variáveis.
- `playbooks/`: Definição das tarefas de manutenção (YAML).
- `ansible.cfg`: Configurações de execução, privilégios e performance.
- `.gitignore`: Proteção de dados sensíveis (IPs e chaves).

## Como Executar
1. Certifique-se de que sua chave pública SSH está presente nos hosts remotos.
2. Configure o inventário em `inventory/hosts.ini`.
3. Execute o Playbook:
   ```bash
   ansible-playbook playbooks/update_system.yml
