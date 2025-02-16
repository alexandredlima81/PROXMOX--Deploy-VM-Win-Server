Fluxo de Deploy de uma VM Windows no Proxmox

Tecnologias Utilizadas

Proxmox: Plataforma de virtualização onde a VM é criada.

Cloud-Init: Utilizado para inicializar e configurar a VM no primeiro boot.

Ansible: Ferramenta de automação usada para interagir com a API do Proxmox e provisionar a VM.

YAML (YML): Formato utilizado para descrever o playbook do Ansible.

QEMU: Hipervisor utilizado pelo Proxmox para executar as VMs.

Cloudbase-Init: Equivalente ao Cloud-Init para Windows, permite configurar a VM automaticamente.

Groovy: Linguagem utilizada no pipeline do Jenkins.

Jenkins: Orquestrador do pipeline de deploy da VM.

Etapas do Fluxo

1. Início do Pipeline no Jenkins

O pipeline solicita ao usuário o nome da VM a ser criada.

O nome da VM é validado para garantir que contenha apenas caracteres permitidos.

O nome validado é armazenado como variável de ambiente para ser utilizado posteriormente.

2. Execução do Playbook Ansible

O pipeline executa o playbook create_vm_from_template_v_3.yml.

O playbook usa a API do Proxmox para clonar uma VM a partir de um template predefinido.

Durante a clonagem, são definidos:

Nome da nova VM.

ID da VM.

Armazenamento a ser utilizado.

Configuração de rede (interface e VLAN).

3. Provisionamento da VM via Ansible

O playbook interage com a API do Proxmox para:

Clonar a VM a partir do template.

Configurar as interfaces de rede.

Ligar a VM após a configuração.

A execução de cada etapa é verificada para garantir que a VM foi criada corretamente.

4. Inicialização da VM com Cloud-Init e Cloudbase-Init

Se a VM é Linux, o Cloud-Init será responsável pela configuração inicial.

Se a VM é Windows, Cloudbase-Init será utilizado para configurar credenciais e aplicações.

5. Validação e Finalização do Pipeline

O pipeline confirma que o playbook foi executado corretamente.

Caso haja falhas, o pipeline exibe os erros encontrados.

Se tudo ocorrer bem, a VM é entregue pronta para uso.

Resumo Visual do Fluxo

Usuário insere o nome da VM (Jenkins - Groovy)

Jenkins executa o playbook Ansible (Ansible - YAML)

Ansible clona a VM (Proxmox - API, QEMU)

Configura interface de rede (Proxmox - API)

Inicia a VM (Proxmox - API, QEMU)

Configuração inicial (Cloud-Init ou Cloudbase-Init)

VM pronta para uso

