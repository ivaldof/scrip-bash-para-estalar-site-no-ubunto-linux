---

# Script de Instalação e Configuração de Site com Apache2

Este script automatiza a instalação do Apache2 e a configuração de um site simples hospedado localmente no Ubuntu/Debian.

## 📜 Descrição

O script verifica se o Apache2 está instalado e, caso não esteja, realiza a instalação. Em seguida, cria uma estrutura de diretórios, clona um repositório com um site HTML/CSS, configura o Apache para servir esse site com um novo Virtual Host e atualiza o arquivo `/etc/hosts` para permitir o acesso via `http://ifrn`.

## ⚙️ Requisitos

* Sistema baseado em Debian (Ubuntu, etc.)
* Permissões de superusuário (`sudo`)
* Git instalado

## 🖥️ Etapas Executadas

1. **Verifica se o Apache2 está instalado**
2. **Instala o Apache2 caso não esteja presente**
3. **Cria a estrutura de diretórios em `/var/www/ifrn/public_html`**
4. **Clona o repositório do site HTML**
5. **Move os arquivos clonados para o diretório do site**
6. **Cria uma configuração de Virtual Host para o Apache**
7. **Ativa o novo site**
8. **Adiciona `127.0.0.1 ifrn` ao arquivo `/etc/hosts`**
9. **Reinicia o serviço do Apache**

## 💡 Como Usar

```bash
chmod +x install_apache_site.sh
sudo ./install_apache_site.sh
```

## 📁 Estrutura Esperada

Após a execução, os arquivos do site estarão disponíveis em:

```
/var/www/ifrn/public_html
```

A configuração do Apache será adicionada em:

```
/etc/apache2/sites-available/ifrn.conf
```

A entrada no arquivo `/etc/hosts` será:

```
127.0.0.1 ifrn
```

## 🌐 Acesso

Após a execução bem-sucedida, abra o navegador e acesse:

```
http://ifrn
```

> 🔒 Dica: caso o navegador não resolva o domínio `ifrn`, certifique-se de que o `/etc/hosts` foi corretamente atualizado e que o Apache está rodando.

## 🛠️ Possíveis Melhorias

* Verificar se o Git está instalado antes de clonar
* Validar se a configuração do Apache foi aplicada corretamente
* Adicionar suporte a outros sistemas operacionais

---

