1. Verifica se o Apache está instalado:
if [ -x /etc/init.d/apache2 ]; then
Essa linha verifica se o arquivo etc/init.d/apache2 é executável./

2. Se o Apache não for encontrado:
echo "apache não encontrado, iniciando a instalação...."
sudo apt-get update
sudo apt-get install apache2 -y
Atualiza os repositórios e instala o Apache.

3. Se o Apache já estiver instalado:
echo "você ja possui um apache instalado"
4. Cria diretórios e clona o site:
sudo mkdir -p /var/www/ifrn/public_html
cd /var/www/ifrn/public_html
sudo git clone https://github.com/matheusmanuel/site-simples-com-html-e-css-.git
sudo cp -r site-simples-com-html-e-css-/* .
sudo rm -rf site-simples-com-html-e-css-/
Cria a pasta do site.
Clona o repositório do GitHub.
Copia os arquivos do site para a pasta principal.
Remove a pasta do repositório clonado (limpeza).
5. Cria um arquivo de configuração para o Apache:
cd /etc/apache2/site-available/
sudo tee ifrn.conf <<EOF
<VirtualHost *:80>
ServerAdmin admin@ifrn
ServerName ifrn
ServerAlias www.ifrn
DocumentRoot /var/www/ifrn/public_html
ErroLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
EOF
Cria o virtual host ifrn.conf.
Define onde está o conteúdo do site.
Define logs.
Erros aqui:

ErroLog → deveria ser ErrorLog.
site-available → o correto é sites-available.
6. Ativa o novo site e configura o hosts:
sudo a2ensite ifrn.conf
sudo echo "127.0.0.1 tfrn" | sudo tee -a /etc/hosts
Ativa o site ifrn.conf.
Adiciona o domínio tfrn no /etc/hosts (possível erro de digitação, o correto seria ifrn).
7. Reinicia o Apache e mostra o status:
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/apache2 status
Reinicia o servidor Apache e mostra se está rodando.

Resumo da função do script:
Verifica se o Apache está instalado (e instala, se necessário).
Cria o diretório para o site.
Baixa e instala um site simples de HTML/CSS.
Cria e ativa um virtual host no Apache.
Configura o domínio local para acessar o site como http://ifrn/.
