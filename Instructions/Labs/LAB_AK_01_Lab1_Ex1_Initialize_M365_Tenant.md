## Locatários do WWL – Termos de uso

Se você estiver recebendo um locatário como parte de uma entrega de treinamento com instrutor, observe que o locatário é disponibilizado com a finalidade de dar suporte aos laboratórios práticos no treinamento com instrutor. 

Os locatários não devem ser compartilhados ou usados para fins fora dos laboratórios práticos. O locatário usado neste curso é um locatário de avaliação e não pode ser usado ou acessado após o fim da aula e não está qualificado para extensão. 

Os locatários não podem ser convertidos em uma assinatura paga. Os locatários obtidos como parte deste curso permanecem a propriedade da Microsoft Corporation e reservamos o direito de obter acesso e a qualquer momento. 

# Roteiro de Aprendizagem 1 – Laboratório 1 – Exercício 1 – Inicializar seu locatário do Microsoft 365 

A Adatum Corporation é uma subsidiária da Contoso Electronics. A Adatum executa seus aplicativos herdados (como o Microsoft Exchange Server 2019) em uma implantação local. Como a nova administradora do Microsoft 365 da Adatum, Holly Dickson, você tem a tarefa de preparar a implantação do Microsoft 365 da Adatum para o Copilot para Microsoft 365. 

Neste exercício, você vai configurar o locatário de avaliação do Microsoft 365 do Adatum e seu instrutor orientará você sobre como obter suas credenciais do Microsoft 365 em seu ambiente de laboratório hospedado. Você usará essas credenciais em todos os outros laboratórios deste curso. 

Em seu ambiente de laboratório, o provedor de hospedagem do laboratório já obteve um locatário de avaliação do Microsoft 365 para você. O provedor de laboratório também criou duas contas de administrador que você usará em seu ambiente de laboratório da VM: 

- Uma conta de administrador local para o ambiente local da Adatum (Adatum\Administrador).
- Uma conta padrão de administrador de locatário no Microsoft 365 (o nome de exibição dessa conta de usuário é MOD Administrator). 

Você fará login no Client 1 PC (LON-CL1) usando a conta local Adatum\Administrator. Quando acessar o Microsoft 365 pela primeira vez, você fará login inicialmente usando a conta de administrador de locatário do Microsoft 365 (MOD Administrator). Em seguida, você vai preparar o locatário do Microsoft 365 da Adatum para o Microsoft Entra ID e para os próximos laboratórios usando alertas de auditoria e o Microsoft Graph PowerShell.


### Tarefa 1: obter suas credenciais do Microsoft 365

Assim que iniciar o laboratório, você poderá acessar o locatário de avaliação gratuito do Microsoft 365 fornecido pelo seu provedor de hospedagem de laboratório no ambiente do Microsoft Virtual Lab. Dentro deste locatário, seu provedor de hospedagem de laboratório criou uma conta de usuário do Microsoft 365 para um administrador de locatário padrão chamado MOD Administrator. O provedor de hospedagem de laboratório atribuiu a essa conta de usuário um nome de usuário e senha exclusivos, e a conta recebeu a função de Administrador global do Microsoft 365. Você deve recuperar esse nome de usuário e senha para que possa entrar no Microsoft 365 dentro do ambiente do Microsoft Virtual Lab. Você também receberá um nome de locatário e um prefixo de locatário. Você também usará essas informações em várias tarefas ao longo dos laboratórios deste curso.

Como esse curso pode ser oferecido por parceiros de aprendizagem que usam diferentes provedores de hospedagem de laboratório autorizados, as etapas exatas envolvidas para recuperar o nome UPN e a ID do locatário correspondentes ao seu locatário podem variar conforme o provedor de hospedagem de laboratório. Portanto, seu instrutor fornecerá as instruções necessárias sobre como recuperar essas informações para o seu curso. <br/>

Você precisa anotar as seguintes informações (fornecidas pelo instrutor) para usar depois:

- **Prefixo do locatário.** Esse prefixo de locatário é para as contas de usuário do Microsoft 365 que você usará para fazer login no Microsoft 365 em todos os laboratórios deste curso. O domínio para cada conta de usuário do Microsoft 365 está no formato de {user alias}@xxxxxZZZZZZ.onmicrosoft.com, onde xxxxxZZZZZZ é o prefixo do locatário. Consiste em duas partes: o prefixo do seu provedor de hospedagem de laboratório (xxxxx; alguns provedores de hospedagem usam um prefixo genérico, como M365x, enquanto outros usam as iniciais da empresa ou alguma outra designação) e a ID do locatário (ZZZZZZ; normalmente um número de 6 dígitos). Anote o valor xxxxxZZZZZZ do prefixo do locatário para usar depois. Quando alguma das etapas do laboratório orientar você a fazer login no Microsoft 365 como uma das contas de usuário (como o MOD Administrator), você deve inserir o valor xxxxxZZZZZZ que obteve aqui como a parte do prefixo do locatário do seu domínio .onmicrosoft.com.

- **Senha do locatário.** Essa é a senha fornecida pelo provedor de hospedagem do laboratório para a conta de administrador de locatário. **Observação:** Você usará essa senha não só para a conta de administrador de locatário, mas também cada uma das contas de usuário predefinidas que são usadas em todos os laboratórios.

- **Nome de domínio personalizado.** O seu provedor de hospedagem de laboratório criou um nome de domínio personalizado para a Adatum. Você usará esse domínio quando adicionar um domínio personalizado ao Microsoft 365 em um exercício de laboratório mais adiante. O nome de domínio está no formato **xxxUPNxxx.xxxCustomDomainxxx.xxx.** Você deve substituir **xxxUPNxxx** pelo número UPN fornecido pelo provedor de hospedagem de laboratório e deve substituir **xxxCustomDomainxxx.xxx** pelo nome de domínio do provedor de hospedagem do laboratório. Por exemplo, vamos supor que seu provedor de hospedagem de laboratório seja a Fabrikam Inc. Se o número UPN atribuído ao seu locatário for AMPVU3a e o nome de domínio personalizado for fabrikam.us, então o nome de domínio do seu novo domínio personalizado será AMPVU3a.fabrikam.us. O seu instrutor fornecerá o número UPN e o nome de domínio personalizado do seu provedor de hospedagem de laboratório.  


### Tarefa 2: configurar o perfil Organizacional da Adatum

Ao longo dos laboratórios deste curso, você desempenhará o papel de Holly Dickson, a administradora do Microsoft 365 da Adatum. Como Holly, você será responsável por configurar o perfil da empresa para seu locatário de avaliação do Microsoft 365. Nesta tarefa, você configurará as opções necessárias para o locatário da Adatum. Como a Holly ainda não criou uma conta de usuário pessoal do Microsoft 365 para si mesma (o que será feito no próximo exercício de laboratório), ela entrará inicialmente no Microsoft 365 usando a conta de administrador de locatário padrão do Microsoft 365 e a senha que foi criada pelo seu provedor de hospedagem de laboratório. Essa conta é a **MOD Administrator**, cujo alias é "admin". O nome de usuário dessa conta é **admin@xxxxxZZZZZZ.onmicrosoft.com** (onde xxxxxZZZZZZ o prefixo do locatário atribuído pelo seu provedor de hospedagem de laboratório); o nome de exibição para essa conta será MOD Administrator.

1. Ao abrir o ambiente de Máquina Virtual do provedor de hospedagem de laboratório, você precisa começar com a Client 1 VM (LON-CL1). Se o ambiente da VM abrir com uma das outras máquinas (como LON-DC1), então mude para **LON-CL1** agora.

2. Faça login na **LON-CL1** com a conta de **Administrador** local que foi criada pelo provedor de hospedagem do laboratório com a senha **Pa55w.rd**. 

3. Na barra de tarefas localizada na parte inferior da tela, selecione o ícone do **Microsoft Edge**. Se for necessário, maximize a janela do navegador quando ela abrir.

4. No navegador Edge, vá para a **Página inicial do Microsoft 365** inserindo a seguinte URL na barra de endereços: **https://portal.office.com** 

5. Na caixa de diálogo **Entrar** que aparece, insira o **Nome de usuário do locatário do Microsoft 365** fornecido pelo seu provedor de hospedagem de laboratório (esta é a conta MOD Administrator). O nome de usuário deve estar no formato de **admin@xxxxxZZZZZZ.onmicrosoft.com**, onde xxxxxZZZZZZ é o prefixo do locatário atribuído pelo seu provedor de hospedagem de laboratório. Selecione **Avançar**. <br/>

    **Observação:** Seu serviço de hospedagem de laboratório pode fornecer a capacidade de selecionar um botão **Digitar texto** (ou equivalente) ao lado dos dados do recurso, como nomes de usuário, senhas, comandos do PowerShell e outros dados que devem ser inseridos ao longo desses laboratórios. Outros provedores de hospedagem de laboratório podem fornecer um método alternativo, como a possibilidade de copiar e colar essas informações. Aproveite essa funcionalidade para não ter que inserir manualmente essas informações. 

6. Na caixa de diálogo **Insira a senha**, insira a **Senha exclusiva do locatário do Microsoft 365** fornecida pelo provedor de hospedagem do seu laboratório e em seguida selecione **Entrar**.

7. Na caixa de diálogo **Continuar conectado?** Marque a caixa de seleção **Não mostrar isso novamente** e selecione **Sim**. Na caixa de diálogo **Salvar senha** que aparece, selecione a opção **Nunca**.

8. Se aparecer uma caixa de diálogo de **Boas-vindas ao Microsoft 365** no meio da tela, não haverá opção para fechá-la. Em vez disso, à direita da janela, selecione o ícone de seta para frente (**>**) duas vezes e, em seguida, selecione o ícone de marca de seleção para avançar pelos slides dessa janela de mensagens. 

9. Se abrir uma janela **Descobrir mais aplicativos** ou **Criar com o Microsoft 365**, feche-a clicando no **X** no canto superior direito da janela. 

10. A página de **Boas-vindas ao Microsoft 365** aparece no navegador Edge na guia **Página Inicial | Microsoft 365**. Esta é a página inicial do Microsoft 365 do MOD Administrator. <br/>

    Observe o ícone que aparece no canto superior direito da tela. Esse ícone representa a conta **MOD Administrator**, que é a conta de administrador de locatário criada pelo seu provedor de hospedagem de laboratório, com a qual você acabou de entrar. As outras contas de usuário do Microsoft 365 que foram criadas pelo provedor de hospedagem de laboratório têm uma imagem associada a cada uma delas; portanto, quando você entrar como qualquer um desses usuários nos próximos laboratórios, a imagem do usuário será exibida em vez das iniciais do usuário. No entanto, quando um usuário como o MOD Administrator não tem nenhuma imagem atribuída, as iniciais do usuário são exibidas no lugar da imagem ou, como nesse caso, um ícone que foi atribuído à conta. <br/>

    Na página de **Boas-vindas ao Microsoft 365**, na lista de ícones de aplicativos que aparecem no painel esquerdo, selecione **Administrador**; isso abre o **Centro de administração do Microsoft 365** em uma nova guia do navegador. 

11. No **Centro de administração do Microsoft 365**, selecione **Mostrar tudo** no painel de navegação e depois em **Configurações**. No grupo de **Configurações**, selecione **Configurações da organização**. 

12. Na janela **Configurações da organização**, a guia **Serviços** é exibida por padrão. Selecione a guia **Perfil da organização**.

13. Na guia **Perfil da organização**, selecione **Informações da organização** na lista de dados do perfil.

14. No painel **Informações da organização** que aparece, insira as seguintes informações: <br/>

    - Nome: **Adatum Corporation** (Observação: a Adatum Corporation é uma subsidiária da Contoso Inc. O locatário de avaliação da Microsoft que seu provedor de hospedagem de laboratório adquiriu para esse laboratório pode ter sido originalmente atribuído à Contoso. Se **Contoso** (ou qualquer outro valor) aparecer como o nome da organização, então mude para **Adatum Corporation**.)

    - Endereço: **555 Main Street**

    - Cidade: **Redmond**

    - Estado ou província: **Washington**

    - CEP ou código postal: **98052**

    - Telefone: não mude

    - Contato técnico: não mude

    - Idioma preferencial: **Inglês**

15. Selecione **Salvar**.

16. Na parte superior do painel de **Informações da organização**, observe a mensagem indicando que as alterações foram salvas. Selecione o **X** no canto superior direito para fechar o painel.

17. Permaneça conectado à **LON-CL1** com o Microsoft Edge aberto no **Centro de administração do Microsoft 365** para realizar a próxima tarefa.

### Tarefa 3: criar um tema personalizado para a equipe do projeto piloto da Adatum

Na tarefa anterior, você aprendeu que, quando alguém está conectado ao Microsoft 365, o sistema exibirá a fotografia dessa pessoa (se fornecida) ou suas iniciais, caso não haja foto. Holly Dickson, administradora do Microsoft 365 da Adatum, não está satisfeita em ver apenas uma imagem ou as iniciais do usuário conectado. Ela quer criar um tema personalizado para os membros de sua equipe do projeto piloto, para que o nome do usuário conectado também seja exibido. Ao final do projeto piloto, se os membros da equipe de projeto piloto preferirem esse design, ela configurará essa mesma opção no tema padrão para que seja aplicado a todos os usuários. 

Os temas personalizados devem ser associados a um ou mais grupos do Microsoft 365. Assim, para implementar essa alteração, Holly deve primeiro criar um grupo do Microsoft 365 para os membros da equipe do projeto piloto. Então, ela poderá criar um tema personalizado associado a esse grupo que permita a configuração de mostrar o nome do usuário conectado. Nesta tarefa, você criará um grupo do Microsoft 365 para os membros da equipe que participarão do projeto piloto do Microsoft 365 da Adatum. Em seguida, você criará um tema personalizado que exibe o nome do usuário conectado e atribuirá a equipe do projeto piloto a este tema. Você também verá outras opções que podem ser configuradas com temas personalizados e poderá fazer as alterações de cores que desejar.

**Observação:** O registro de equipe que você criar para a equipe do projeto piloto do Microsoft 365 também será usado nos próximos exercícios de laboratório nos quais você criará uma política de Acesso Condicional para habilitar a Autenticação Multifator. Você habilitará a MFA para todos os usuários, exceto para os membros da equipe de projeto piloto.

1. Você ainda deve estar logado no LON-CL1 com a conta local **adatum\administrador** e, no navegador Edge, ainda deve estar logado no Microsoft 365 como **MOD Administrator**. 

2. No **Centro de administração do Microsoft 365**, selecione **Equipes e grupos** no painel de navegação e, em seguida, abaixo dele, selecione **Equipes e grupos ativos**. 

3. Na página **Equipes e grupos ativos**, há uma aba para visualizar cada um dos tipos de grupo. A guia **Equipes e grupos do Microsoft 365** é exibida por padrão. Essa guia mostra os grupos do Microsoft 365 existentes.  <br/>

    Selecione a opção **+Adicionar um grupo do Microsoft 365** que aparece na barra de menu acima da lista de grupos do Teams e do Microsoft 365. Isso inicia o assistente **Adicionar um grupo do Microsoft 365**. 

4. No assistente **Adicionar um grupo do Microsoft 365**, na página **Configurar o básico**, insira **Projeto piloto do M365** no campo **Nome**, e depois insira os **Membros da equipe do projeto piloto do Microsoft 365** no campo **Descrição** (observação: mesmo que você não insira uma descrição, ainda precisará selecionar este campo para habilitar o botão **Próximo**). Selecione **Avançar**.

5. Agora você atribuirá o MOD Administrator como proprietário do grupo **Projeto piloto do M365**. Na janela **Atribuir proprietários**, selecione **+Atribuir proprietários**.
    
6. No painel **Atribuir proprietários** que aparece, marque a caixa ao lado de **MOD Administrator** e selecione o botão **Adicionar (1)** na parte inferior do painel.

7. Na página **Atribuir proprietários**, o MOD Administrator deve aparecer como proprietário do grupo. Selecione **Avançar**.

8. Agora você vai adicionar membros ao grupo do projeto piloto do M365. Na página **Adicionar membros**, selecione **+Adicionar membros**.

9. No painel **Adicionar membros** que surge, marque as caixas de seleção ao lado dos seguintes usuários (em ordem alfabética): **Alex Wilber**, **Allan Deyoung**, **Diego Siciliani**, **Isaiah Langer**, **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**, **MOD Administrator**, **Nestor Wilke**, e **Patti Fernandez**. Depois, selecione o botão **Adicionar (10)** na parte inferior do painel.

10. Na página **Adicionar membros**, confira se esses 10 usuários estão listados como membros do grupo. Se faltar alguém, selecione **+Adicionar membros** e adicione qualquer um dos 10 usuários que não foram incluídos anteriormente. Quando todos os 10 usuários aparecerem nesta página, selecione **Próximo**.

11. Na página **Editar configurações**, preencha as informações a seguir: <br/>

    - Insira **m365pilotproject** no campo **Endereço de email do grupo**.
    - No campo **Privacidade**, selecione **Privado**.
    - Na seção **Adicionar o Microsoft Teams ao seu grupo**, verifique se a caixa de seleção **Criar uma equipe para esse grupo** está marcada (maque-a se estiver em branco) e selecione **Próximo**.

12. Na página **Revisar e finalizar adição do grupo**, verifique as informações que você inseriu. Se precisar corrigir alguma coisa, selecione **Editar** na área específica, faça as correções necessárias e selecione **Próximo** para voltar à página. Depois que tudo estiver certo, selecione **Criar grupo**.

13. Quando a janela **Grupo do projeto piloto M365 criado** aparecer, veja o comentário no topo da página informando que pode levar até 5 minutos para o novo grupo aparecer na lista de Grupos ativos.  </br>

    Selecione **Fechar**. Isso te levará de volta à página **Equipes e grupos ativos**, que deve mostrar a guia **Grupos do Microsoft 365 e Teams**. Como o grupo do projeto piloto do M365 é um grupo do Microsoft 365, ele deverá aparecer nesta guia em algum momento. Se necessário, selecione a opção **Atualizar** na barra de menu até que o grupo apareça na lista de grupos do Microsoft 365 e Teams.

14. No **Centro de administração do Microsoft 365**, na seção **Configurações** do painel de navegação, selecione**Configurações da organização**. 

15. Na página **Configurações da organização**, selecione a guia **Perfil da organização**.

16. Na lista de dados do perfil da organização, selecione **Temas personalizados**.

17. No painel **Personalizar o Microsoft 365 para sua organização** que aparece, você pode personalizar o tema padrão que os usuários veem ao entrar no Microsoft 365 e adicionar mais temas personalizados. Selecione a opção **+Adicionar tema**.

18. No painel **Novo tema do grupo** que surge, a guia **Geral** é mostrada por padrão. Insira **Tema do projeto piloto do M365** no campo **Nome**.

19. Selecione o campo **Grupos**. Na lista de grupos que aparece, selecione **Projeto piloto do M365** se ele estiver na lista. <br/>

    **Observação:** Se **Projeto piloto M365** não estiver na lista de grupos, então insira **M365** no campo **Grupos**. Uma caixa de resultados da pesquisa deve aparecer mostrando o grupo **Projeto piloto do M365**. Selecione **Projeto piloto do M365**. 

20. Marque a caixa de seleção **Mostrar o nome de exibição do usuário**. Essa é a configuração que Holly quer personalizar para os membros da equipe do projeto piloto do M365. Esta opção mostra o nome do usuário ao lado das iniciais deles em cada cabeçalho de janela.
 
21. Selecione **Salvar**. Feche o painel **Tema do projeto piloto do M365** assim que suas alterações forem salvas. 

22. Selecione o ícone **Atualizar** no topo da tela, à esquerda da barra de endereços. Depois que a tela atualizar, veja como o nome **MOD Administrator** aparece à esquerda do círculo com o ícone de megafone. Quando os membros da equipe do projeto piloto do Microsoft 365 entrarem no Microsoft 365, o nome de usuário deles agora aparece à esquerda da imagem de perfil (ou, neste caso, um ícone de um megafone) ou das iniciais devido ao tema personalizado que você acabou de criar.

23. Na lista de dados do perfil da organização, selecione **Temas personalizados**.

24. No painel **Personalizar o Microsoft 365 para sua organização** que aparece, veja como ele mostra o **Tema padrão** e o **Tema do projeto piloto do M365**. Selecione o **Tema padrão**. 

25. No painel **Tema padrão**, perceba como a opção **Mostrar o nome de exibição do usuário** não está selecionada para o tema padrão. Se a Holly decidir mais tarde tornar a opção **Mostrar o nome de exibição do usuário** uma funcionalidade permanente, ela selecionará essa opção no painel **Tema padrão** para que se aplique a todos os usuários da Adatum, e excluirá o **Tema do projeto piloto do M365**. <br/>

    Feche o painel **Tema personalizado**.

26. Permaneça conectado à **LON-CL1** com o Microsoft Edge aberto no **Centro de administração do Microsoft 365** para realizar a próxima tarefa.

### Tarefa 4 – Instalar o Microsoft Graph PowerShell 

O Microsoft Graph PowerShell é necessário para realizar várias tarefas de configuração durante a instalação do Microsoft 365. Como os próximos exercícios de laboratório farão uso do Windows PowerShell para executar essas tarefas, o primeiro passo é instalar o módulo do Microsoft Graph PowerShell. Este módulo permite que você realize várias tarefas de administração de usuários e da organização do Microsoft 365 através do PowerShell. É ótimo para tarefas em massa, como redefinições de senha, políticas de senha, gerenciamento de licenças e relatórios, entre outros.  

1. Na LON-CL1, você ainda deve estar conectado como a conta local **adatum\administrador**. Para instalar o Microsoft Graph PowerShell, você precisa abrir uma instância elevada do **Windows PowerShell**. Digite **power** na caixa Pesquisar, que fica no canto inferior esquerdo da barra de tarefas. Na lista de resultados da pesquisa, clique com o botão direito em **Windows PowerShell** (não selecione Windows PowerShell ISE) e selecione a opção **Executar como administrador** no menu que aparecer. 

2. Maximize sua janela do PowerShell. No **Windows PowerShell**, digite o comando a seguir no prompt de comando para instalar o módulo do Microsoft Graph PowerShell na Galeria do PowerShell e pressione Enter: <br/>

        Install-Module Microsoft.Graph -Scope CurrentUser

3. Você será solicitado a confirmar se deseja instalar o módulo de um repositório não confiável (PSGallery). Insira **A** para selecionar **[A] Sim para Todos** e pressione Enter.  <br/>

    **Observação:** sua resposta iniciará a instalação de todos os submódulos do Microsoft Graph. Após as mensagens de instalação de cada submódulo serem exibidas, ainda levará cerca de 5 a 10 minutos adicionais para concluir a instalação do Microsoft Graph PowerShell. Durante esse tempo, o cursor continuará piscando abaixo da mensagem de repositório não confiável. <br/>

    **Este pode ser um bom momento para fazer uma pausa.**

4. Um prompt de comando aparecerá assim que o Microsoft Graph PowerShell for instalado. Agora você verá a lista de sub-módulos que foram instalados. Para fazer isso, execute o comando a seguir:

        Get-InstalledModule Microsoft.Graph.* | select *name*

5. Verifique se a lista inclui os três submódulos a seguir, que serão usados nos próximos exercícios de laboratório: 

    - Microsoft.Graph.Groups
    - Microsoft.Graph.Identity.DirectoryManagement
    - Microsoft.Graph.Users
    
    Se todos os três sub-módulos estiverem presentes na lista, prossiga para a próxima etapa. No entanto, se algum um desses três sub-módulos não aparecer na lista, execute o seguinte comando do PowerShell para instalar manualmente o sub-módulo que está faltando:

        Install-Module -Name <module name> -Scope CurrentUser

    Por exemplo, se o módulo Microsoft.Graph.Identity.DirectoryManagement não foi instalado, você deverá executar o seguinte comando:

        Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement

6. As configurações de política de execução do PowerShell determinam quais scripts do PowerShell podem ser executados em um sistema Windows. Definir essa política como **Irrestrita** permite que Holly carregue todos os arquivos de configuração e execute todos os scripts. No prompt de comando, digite o seguinte comando e pressione Enter:   <br/>

        Set-ExecutionPolicy unrestricted

    ‎Se for solicitado que você confirme se deseja alterar a política de execução, insira **A** para selecionar **[A] Sim para Todos.** 

7. Mantenha a janela do PowerShell aberta, mas minimizada. Você a usará em um exercício de laboratório mais adiante.


**Parabéns! Você concluiu todas as etapas para inicializar o locatário do laboratório. Agora você está pronto para realizar os demais exercícios de laboratório.**

# Fim do Laboratório 1
