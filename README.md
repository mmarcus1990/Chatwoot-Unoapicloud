# Chatwoot-Unoapicloud

---------------------------------------------------------------------------------------------------------------------------
Manual de Instalação ChatWoot

sudo apt update && apt upgrade -y

wget https://get.chatwoot.app/linux/install.sh

chmod +x install.sh

./install.sh --install

Use as opções abaixo

yes

chatwoot.dominio.com.br

contato@dominio.com.br

yes para todos

----------------------------------------------------------------------------------------------------------------------------

Alterando Idioma e ativando sua tela de cadastro

cd /home/chatwoot/chatwoot

nano .env

Altere a linha

DEFAULT_LOCALE=pt_BR

ENABLE_ACCOUNT_SIGNUP=true

sudo systemctl restart chatwoot.target

Acesse: seudominio.com.br

Faça seu cadastro

---------------------------------------------------------------------------------------------------------------------------------

Habilitando configurações ocultas do Chatwoot

No banco de dados PostgreSQL

sudo -u postgres psql

\c chatwoot_production

update installation_configs set locked = false;

\q

--------------------------------------------------------------------------------------------------------------------------------------

NOMES CHATWOOT TERMOS E POLITICA DE PRIVACIDADE

Acesse super Admin

https://seudominio.com.br/super_admin

Opção>installation_configs

LOGO

LOGO_THUMBNAIL

NOMES CHATWOOT:


Alterando nomes na plataforma

INSTALLATION_NAME

BRAND_NAME

TERMOS E POLITICA DE PRIVACIDADE

TERMS_URL

PRIVACY_URL

BRAND_URL

WIDGET_BRAND_URL

-----------------------------------------------------------------------------------------------------------------------------------

Manual de Instalação UNOAPI

sudo apt update && apt upgrade -y

sudo apt-get install -y libgbm-dev wget unzip fontconfig locales gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils

git clone https://github.com/clairton/unoapi-cloud

cd unoapi-cloud

chmod 777 data

npm install pm2 -g

yarn install

----------------------------------------------------------------------------------------------------------------------------------------

Cole codigo abaixo

vim .env

WEBHOOK_URL=https://urldosite/webhooks/whatsapp
WEBHOOK_TOKEN=Coloque Token Agente aqui
WEBHOOK_HEADER=api_access_token
BASE_URL=http://localhost:9876
IGNORE_GROUP_MESSAGES=false
IGNORE_BROADCAST_STATUSES=true
IGNORE_BROADCAST_MESSAGES=false
IGNORE_HISTORY_MESSAGES=true
IGNORE_OWN_MESSAGES=false
IGNORE_YOURSELF_MESSAGES=true
COMPOSING_MESSAGE=true
REJECT_CALLS=Olá! Sinto muito, mas não consigo responder chamadas neste momento. Por favor, deixe uma mensagem com seu nome e número de telefone, e eu retornarei assim que possível. Obrigado!
REJECT_CALLS_WEBHOOK=Olá! Recebi sua chamada, mas não consigo atendê-la pessoalmente no momento. No entanto, sua mensagem é importante para mim. Por favor, deixe seu nome, número de telefone e motivo da ligação, e entrarei em contato o mais breve possível. Agradeço sua compreensão!
SEND_CONNECTION_STATUS=true
UNOAPI_BASE_STORE=./data

yarn build

pm2 start dist/index.js --name UNOAPI

EXECUTE COMANDO ABAIXO PARA NÃO CAIR QUANDO REINICIAR A VPS

sudo pm2 startup ubuntu -u root && sudo pm2 startup ubuntu -u root --hp /root && sudo pm2 save

--------------------------------------------------------------------------------------------------------

Adicionar URL abaixo no .env do chatwoot

cd /home/chatwoot/chatwoot

vim .env

WHATSAPP_CLOUD_BASE_URL=http://localhost:9876

--------------------------------------------------------------------------------------------------------

Recompilando seu Chatwoot

sudo -i -u chatwoot

cd chatwoot

git checkout master && git pull

rvm reinstall ruby-3.1.3

rvm use 3.1.3 --default

bundle

yarn

rake assets:precompile RAILS_ENV=production

RAILS_ENV=production bundle exec rake db:migrate

exit

systemctl daemon-reload

systemctl restart chatwoot.target

-------------------------------------------------------------------------------------------------------------------------------------


Acesse ChatWoot

Caixas de Entrada

Adicionar Caixas de Entrada

Canal do whatsapp

Nome da Caixa de Entrada (Adicione o que desejar)

Número de telefone (+Número de telefone)

ID do número de telefone (+Número de telefone )

ID da Conta de Negócios (Número de telefone )

Chave da API (any)

 
