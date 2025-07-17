Configuração de login do Maui Firebase Google
Artigo/Blog
Configurei com sucesso o Google Sign-In usando o Firebase para meu aplicativo .NET MAUI. Abaixo, um guia passo a passo que você pode seguir para replicar a configuração.

https://github.com/branux/RegistrarAppFirebaseGoogle.git

🔧 1. Crie um projeto do Firebase Vá para o Firebase Console e crie um novo projeto.

🏗 2. Registre seu aplicativo no Firebase Em Configurações do projeto > Geral, clique em Adicionar aplicativo e escolha a plataforma apropriada (por exemplo, Android).

Insira o nome do seu pacote e outros detalhes necessários. (<ApplicationId>com.companyname.mymaui</ApplicationId>)

🔑 3. Gerar certificado SHA-1 (somente Android) Para gerar a chave SHA-1, execute o seguinte comando na pasta do seu projeto:

"C:\Program Files\Java\jdk-24\bin\keytool.exe" -genkeypair -v -keystore mauiapp2.keystore -alias mauiapp2 -keyalg RSA -keysize 2048 -validity 10000

Para visualizar a impressão digital SHA-1:

keytool -v -list -keystore mauiapp2.keystore Em seguida, vá para Firebase Console > Configurações do projeto > Geral e adicione o SHA-1 em Impressões digitais do certificado SHA.

🔐 4. Habilite a autenticação do Google no Firebase Vá para Autenticação > Método de login no Firebase.

Ative o login do Google.

Não há necessidade de configurar o ID do cliente ou o SDK manualmente

Para sua informação: o Firebase cria automaticamente um projeto correspondente no Google Cloud Console.

📥 5. Adicione google-services.json ao seu projeto Em Firebase Console > Configurações do projeto, baixe o arquivo google-services.json para seu aplicativo.

Adicione-o ao seu projeto MAUI no diretório Recursos.

🔧 6. Configure o OAuth no Google Cloud Console. Acesse o Google Cloud Console, procure seu projeto do Firebase na caixa de pesquisa superior (o mesmo nome com o qual você registrou seu aplicativo no Firebase).

Navegue até APIs e Serviços > Credenciais. (Já deve haver muitas credenciais configuradas)

Clique em Criar credenciais > ID do cliente OAuth e escolha Aplicativo Web.

Não é necessário definir URIs de redirecionamento. Basta salvar e copiar o ID do Cliente gerado.

🧩 7. Use o ID do cliente no seu projeto MAUI Adicione o OAuth ClientId como um googleRequestIdToken no seu código.
