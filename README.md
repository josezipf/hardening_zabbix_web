# 📌 Ansible Role: Hardening Zabbix Web (Apache Security Hardening)

![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=flat&logo=ansible&logoColor=white)  
![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=flat&logo=apache&logoColor=white)

---

## ⚠️ ATENÇÃO

**❗ Essa role realiza modificações de segurança no Apache que podem impactar o funcionamento de aplicações, módulos e integrações existentes no servidor.**

Ela altera vários arquivos de configuração e aplica políticas restritivas que podem gerar conflitos dependendo do ambiente.

👉 **Recomendamos fortemente testar primeiro em um ambiente de homologação antes de aplicar em produção.**  

Faça um backup das configurações atuais e valide cuidadosamente após a aplicação.

---

## 🔒 Descrição

Role para endurecimento de segurança do Apache em ambientes Zabbix, aplicando configurações de headers HTTP, permissões de arquivos e redirecionamento HTTPS obrigatório.

---

## 🚀 Funcionalidades

✔️ Configura headers de segurança (CSP, HSTS, X-Frame-Options)  
✔️ Remove arquivos padrão do Apache (`index.html` / `index.php`)  
✔️ Ajusta permissões da pasta Zabbix (`0755` para diretórios, `0644` para arquivos)  
✔️ Força redirecionamento HTTP → HTTPS  
✔️ Desativa métodos inseguros (TRACE) e `ServerSignature`  

---

## 📦 Pré-requisitos

- Ansible ≥ 2.9  
- Ubuntu (testado em **Noble**)  
- Apache2 instalado  

---

## 🛠️ Como Usar (Teste Rápido)

### 1️⃣ Crie um playbook de teste (`test.yml`):

```yaml
---
- hosts: localhost  # Ou seu grupo de servidores Zabbix
  become: true      # Executa como root
  vars:
    zabbix_server_name: "zabbix.seudominio.com"  # Altere para seu domínio
  
  roles:
    - role: hardening_zabbix_web
```

## 📂 Estrutura da Role

```
hardening_zabbix_web/
├── defaults/
├── tasks/
├── templates/
│   ├── apache_security.conf.j2
│   ├── security-headers.conf.j2
│   └── redirect-http-to-https.conf.j2
└── handlers/
```

## 📄 Licença
MIT — veja o arquivo LICENSE no repositório.

