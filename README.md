# Exemplo de Solicitação de Firebase

Esse projeto tem como exibir o uso do Firebase para enviar notificações no celular.

Esse projeto está configurado para enviar de uma aplicação Firebase de Testes.

### Pré requisitos

    - Interpretador PHP na sua máquina.
    - Google Cloud CLI [](gcloud) Beta.
    
### Instalação
    
    - Descompacte a pasta do projeto em alguma pasta do seu computador.
    - Defina a pasta da instalação do PHP no PATH do computador (Exemplo do xampp: C:/xampp/php).
    
### Executar em maquina local

    - Na pasta do projeto execute o prompt de comando.
    - Execute "php artisan serve" para executar o projeto no endereço http://localhost:8000.
    
### Subir na Google Cloud via App Engine
    
    - Realize as configurações necessarias para apontar para o projeto correto.
    - Na pasta do projeto execute o prompt de comando.
    - Execute "gcloud beta app deploy -q --no-cache".
    - Aguarde até realizar o deploy do projeto.
    
## Rotas de API disponiveis

Todas as rotas devem ser feitas sobre o método **POST**.
    
**Enviar para um dispositivo**

        <endereco-do-site>/api/v1/fcm/send_message/unique_device
        
**Enviar para um Tópico(Grupo)**

        <endereco-do-site>/api/v1/fcm/send_message/topic
        
**Inscrever um dispositivo num Tópico**

        <endereco-do-site>/api/v1/fcm/topic/register
        
**Desinscrever um dispositivo num Tópico**
    
        <endereco-do-site>/api/v1/fcm/topic/unregister
        
### Detalhes de cada Rota

**Enviar para um dispositivo**

* Envia uma notificação para único dispositivo.

        URL: /api/v1/fcm/send_message/unique_device
        MÉTODO: POST
        PARÂMETROS:
            - token:
                tipo: string
                descrição: Token que é gerado quando é instalado o aplicativo.
                aceita vários valores: Não.
                exemplo: cgBCgTk0TviEjP9UExpujY:APA91bEJ7HuLUrNK8RipA1Acoqf5R_23sA07Dg6za2wnba5lmzVfTupHhHJt5AdH2VECzH2AkMpR6guO-k2ekREn8iois24I5jpFeK0WGlRNye03Q8okbi6f7ZsfB8DT0cj4HK1eY8J5
            - titleNotification:
                tipo: string
                descrição: Titulo da notificação enviada.
                aceita vários valores: Não.
                exemplo: Teste Laravel no App Engine
            - bodyNotification:
                tipo: string
                descrição: Texto da notificação enviada.
                aceita vários valores: Não.
                exemplo: Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit magnam reiciendis totam. Culpa eligendi eum, hic id, ipsum magni minima molestias numquam optio placeat rem sunt tempora velit voluptates voluptatibus!    

**Enviar para um Tópico(Grupo)**

* Envia uma notificação para um grupo de usuários (Ideal para enviar todos da empresa)

        URL: /api/v1/fcm/send_message/topic
        MÉTODO: POST
        PARÂMETROS:
            - topic:
                tipo: string
                descrição: Nome dado no momento que registra o dispositivo no Firebase.
                aceita vários valores: Não.
                exemplo: Ponttonline
            - titleNotification:
                tipo: string
                descrição: Titulo da notificação enviada.
                aceita vários valores: Não.
                exemplo: Teste Laravel no App Engine
            - bodyNotification:
                tipo: string
                descrição: Texto da notificação enviada.
                aceita vários valores: Não.
                exemplo: Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit magnam reiciendis totam. Culpa eligendi eum, hic id, ipsum magni minima molestias numquam optio placeat rem sunt tempora velit voluptates voluptatibus!
                
**Inscrever um dispositivo num Tópico**

* Registra um dispositivo num tópico:

        URL: /api/v1/fcm/topic/register
        MÉTODO: POST
        PARÂMETROS:
            - topic:
                tipo: string
                descrição: Nome dado no momento que registra o dispositivo no Firebase.
                aceita vários valores: Não.
                exemplo: Ponttonline
            - devices[]:
                tipo: string
                descrição: Token que é gerado quando é instalado o aplicativo.
                aceita vários valores: Sim.
                exemplo: cgBCgTk0TviEjP9UExpujY:APA91bEJ7HuLUrNK8RipA1Acoqf5R_23sA07Dg6za2wnba5lmzVfTupHhHJt5AdH2VECzH2AkMpR6guO-k2ekREn8iois24I5jpFeK0WGlRNye03Q8okbi6f7ZsfB8DT0cj4HK1eY8J5
        
**Desinscrever um dispositivo num Tópico**

* Desregistra um dispositivo num tópico:
    
        URL: /api/v1/fcm/topic/unregister
        MÉTODO: POST
        PARÂMETROS:
            - topic:
                tipo: string
                descrição: Nome dado no momento que registra o dispositivo no Firebase.
                aceita vários valores: Não.
                exemplo: Ponttonline
            - devices[]:
                tipo: string
                descrição: Token que é gerado quando é instalado o aplicativo.
                aceita vários valores: Sim.
                exemplo: cgBCgTk0TviEjP9UExpujY:APA91bEJ7HuLUrNK8RipA1Acoqf5R_23sA07Dg6za2wnba5lmzVfTupHhHJt5AdH2VECzH2AkMpR6guO-k2ekREn8iois24I5jpFeK0WGlRNye03Q8okbi6f7ZsfB8DT0cj4HK1eY8J5
