# Instalação Native PHP (PHP 8.4.18)

Está documentação orienta a instalação completa do ambiente Laravel de desenvolvimento e produção.

Versão utilizada: PHP 8.4.18

```ini
    ; ============================================================
    ; php.ini otimizado para XAMPP + PHP 8.4 + Composer + Laravel
    ; Localização: C:\xampp\php\php.ini
    ; ============================================================

    [PHP]

    ; --- Engine ---
    engine = On
    short_open_tag = Off
    precision = 14
    serialize_precision = -1

    ; --- Memória e Tempo ---
    memory_limit = 512M
    max_execution_time = 120
    max_input_time = 120
    max_input_vars = 10000

    ; --- Output Buffering ---
    output_buffering = 4096
    implicit_flush = Off
    zlib.output_compression = Off

    ; --- Erros (desenvolvimento) ---
    error_reporting = E_ALL
    display_errors = On
    display_startup_errors = On
    log_errors = On
    ignore_repeated_errors = Off
    report_memleaks = On
    error_log = "C:\xampp\php\logs\php_error_log"

    ; --- Upload de arquivos ---
    file_uploads = On
    upload_max_filesize = 100M
    max_file_uploads = 50
    post_max_size = 100M
    upload_tmp_dir = "C:\xampp\tmp"

    ; --- URLs e Streams ---
    allow_url_fopen = On
    allow_url_include = Off
    default_socket_timeout = 60

    ; --- Segurança ---
    expose_php = Off
    disable_functions =
    disable_classes =

    ; --- Misc ---
    variables_order = "GPCS"
    request_order = "GP"
    register_argc_argv = Off
    auto_globals_jit = On
    zend.enable_gc = On
    zend.assertions = 1
    zend.exception_ignore_args = Off
    zend.exception_string_param_max_len = 15

    ; ============================================================
    ; Diretório das extensões (XAMPP)
    ; ============================================================
    extension_dir = "C:\xampp\php\ext"

    ; ============================================================
    ; ÚNICA extensão externa confirmada no seu XAMPP PHP 8.4
    ; Todas as outras (bcmath, curl, openssl, pdo_mysql, mbstring,
    ; gd, intl, sodium, sqlite3, zip, etc.) são built-in nesta
    ; versão e NÃO devem ser declaradas aqui.
    ; ============================================================
    extension=bz2
    extension=openssl
    extension=fileinfo
    extension=zip

    ; OPcache (built-in no PHP 8.4, apenas configurar)
    zend_extension=opcache

    [opcache]
    opcache.enable=1
    opcache.enable_cli=1
    opcache.memory_consumption=256
    opcache.interned_strings_buffer=16
    opcache.max_accelerated_files=20000
    opcache.revalidate_freq=2
    opcache.validate_timestamps=1
    opcache.save_comments=1

    ; ============================================================
    ; Caminhos (XAMPP)
    ; ============================================================
    sys_temp_dir = "C:\xampp\tmp"
    doc_root = "C:\xampp\htdocs"
    include_path = ".;C:\xampp\php\PEAR"

    ; ============================================================
    ; Timezone
    ; ============================================================
    [Date]
    date.timezone = America/Sao_Paulo

    ; ============================================================
    ; Mail (Mercury/sendmail do XAMPP)
    ; ============================================================
    [mail function]
    SMTP = localhost
    smtp_port = 25
    sendmail_from = you@example.com
    ; sendmail_path = "\"C:\xampp\sendmail\sendmail.exe\" -t"
    mail.add_x_header = Off

    ; ============================================================
    ; Session
    ; ============================================================
    [Session]
    session.save_handler = files
    session.save_path = "C:\xampp\tmp"
    session.use_strict_mode = 1
    session.use_cookies = 1
    session.use_only_cookies = 1
    session.name = LARAVELSESSION
    session.cookie_httponly = 1
    session.cookie_samesite = "Lax"
    session.gc_divisor = 1000
    session.gc_maxlifetime = 7200
    session.serialize_handler = php

    ; ============================================================
    ; MySQL / PDO
    ; ============================================================
    [MySQLi]
    mysqli.max_persistent = -1
    mysqli.allow_persistent = On
    mysqli.max_links = -1
    mysqli.default_port = 3306
    mysqli.default_socket =
    mysqli.default_host = localhost

    [Pdo_mysql]
    pdo_mysql.default_socket =

    ; ============================================================
    ; mbstring
    ; ============================================================
    [mbstring]
    mbstring.language = neutral

    ; ============================================================
    ; SOAP
    ; ============================================================
    [soap]
    soap.wsdl_cache_enabled = 1
    soap.wsdl_cache_dir = "C:\xampp\tmp"
    soap.wsdl_cache_ttl = 86400
    soap.wsdl_cache_limit = 5

    [Tidy]
    tidy.clean_output = Off

    [ldap]
    ldap.max_links = -1

    [CLI Server]
    cli_server.color = On
```