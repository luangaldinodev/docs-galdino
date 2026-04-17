# Instalação Laravel (Windows + WSL + Docker + Ubuntu)

Está documentação orienta a instalação completa do ambiente Laravel de desenvolvimento e produção.

## Requisitos

* WSL 2
* Docker desktop

## 1. Instalação do linux Ubuntu via WSL

**1. Abra o CMD ou PowerShell como administrador e execute o seguinte comando:**

``` 
    wsl --install
```
O Windows baixará e instalará automaticamente o WSL com a distribuição Ubuntu como padrão.

**2. Após a instalação, reinicie o computador.**

**3. Após a reinicialização, abra o CMD ou PowerShell como administrador e execute:**

```
    wsl -d Ubuntu
```
Isso garantirá que o Ubuntu seja iniciado corretamente dentro do WSL.

Ou procure por "Ubuntu" no menu iniciar do Windows.

## 2. Instalação de pacotes essenciais 
**1. Atualize os pacotes do sistema.**

```bash
    sudo apt update && sudo apt upgrade -y
```

**2. Instale o PHP, Composer e outras dependências necessárias para o Laravel.**

```bash
    sudo apt install php8.3-cli php8.3-common php8.3-mbstring php8.3-xml php8.3-bcmath php8.3-curl php8.3-mysql php8.3-zip php8.3-readline php8.3-gd php8.3-pgsql unzip curl git composer -y
```
Para instalar outra versão do PHP, basta substituir `php8.3` pela versão desejada (ex: `php8.2`). Ou peça ajuda ao ChatGPT para instalar a versão específica do PHP.

**3. Verifique a instalação do PHP e do Composer.**

```bash
    php -v
    composer -V
```
## 3. Laravel Installer

**1. Instale o Laravel Installer globalmente usando o Composer.**

```bash
    composer global require laravel/installer
```

**2. Adicione o diretório do Laravel Installer ao PATH.**

```bash
    echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
```

o `source ~/.bashrc` recarrega o arquivo de configuração do shell para que as alterações no PATH tenham efeito imediato.

**3. Verifique a instalação do Laravel Installer.**

```bash
    laravel -V
```

## 4. Crie ou acesse seu projeto Laravel

**1. Para criar um novo projeto Laravel, execute:**

```bash
    laravel new nome-do-projeto
```

**2. Para acessar um projeto Laravel existente, navegue até o diretório do projeto:**

```bash
    cd caminho/para/seu/projeto
```

## 5. Configuração do Docker usando Laravel Sail

A partir deste ponto, você pode usar a documentação oficial do Laravel Sail para configurar o ambiente de desenvolvimento usando Docker.

[Documentação do Laravel Sail - Laravel 12](https://laravel.com/docs/12.x/sail).

**1. Dentro do diretório do seu projeto Laravel, instale o Laravel Sail usando o Composer:**

```bash
    composer require laravel/sail --dev
```

O Laravel Sail é instalado automaticamente com todas as novas aplicações Laravel, para que você possa começar a usá-lo imediatamente.

**2. Publique os arquivos de configuração do Sail:**

```bash
    php artisan sail:install
```

**3. Inicie os containers do Docker usando o Sail:**

Certifique-se de configurar corretamente o nome do banco de dados. Usuário, senha, e outras variáveis de ambiente no arquivo `.env` o Laravel Sail configura automaticamente, mas é importante verificar se estão corretas.

```bash
    ./vendor/bin/sail up -d
```

**4. Rode as migrações para configurar o banco de dados:**

```bash
    ./vendor/bin/sail artisan migrate
```

## Referências

[Documentação do Laravel Sail - Laravel 12](https://laravel.com/docs/12.x/sail)

[Instalação do WSL 2 no Windows 10/11](https://docs.microsoft.com/pt-br/windows/wsl/install)

[How to Install Docker and Laravel on Windows (WSL + Ubuntu Setup)](https://www.youtube.com/watch?v=7hf4EDU9S6g)