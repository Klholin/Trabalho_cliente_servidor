# Trabalho de Cliente-Servidor

Para que o programa rode corretamente, é necessário criar os certificados válidos para o servidor.
obs: garanta que openssl esteja baixado em sua máquina e que a basta bin dele esteja nas variáveis de ambiente

## Passo a Passo

1. **Criar um arquivo `openssl.cnf`:**  
   - Abra um editor de texto (como Bloco de Notas no Windows ou `nano` no Linux).  
   - Insira o seguinte conteúdo no arquivo:

     [ req ]
     distinguished_name = req_distinguished_name
     x509_extensions = v3_req
     prompt = no

     [ req_distinguished_name ]
     CN = 127.0.0.1

     [ v3_req ]
     subjectAltName = @alt_names

     [ alt_names ]
     IP.1 = 127.0.0.1
   

   - Salve o arquivo como `openssl.cnf` no diretório do seu projeto.

2. **Gerar o certificado e a chave privada:**  
   Execute o seguinte comando no terminal ou Git Bash no diretório onde o arquivo `openssl.cnf` está localizado:
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365 -nodes -config openssl.cnf
