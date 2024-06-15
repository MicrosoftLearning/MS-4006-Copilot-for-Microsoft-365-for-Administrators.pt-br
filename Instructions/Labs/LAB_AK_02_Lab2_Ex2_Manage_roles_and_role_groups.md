# Roteiro de Aprendizagem 2, Laboratório 2, Exercício 2: Gerenciar funções e grupos de funções

Neste exercício, você continuará representando seu papel de Holly Dickson, a nova Administradora do Microsoft 365 da Adatum. Como parte do projeto piloto do Microsoft 365 da Adatum, você irá gerenciar a delegação de administração atribuindo funções de Administrador do Microsoft 365 a várias das contas de usuário do Microsoft 365 que foram criadas pelo seu provedor de hospedagem do laboratório. Este exercício irá proporcionar experiência no uso de três métodos diferentes para atribuir essas funções: 1) atribuindo uma função diretamente a uma conta de usuário no Centro de administração do Microsoft 365; 2) criando um grupo de funções, atribuindo funções a ele e, em seguida, atribuindo o grupo de funções a um usuário no Centro de administração do Microsoft 365; e 3) atribuindo uma função a um usuário usando o Windows PowerShell. Depois de atribuir as funções de Administrador do Microsoft 365 a várias das contas de usuário existentes, você irá testar essas atribuições verificando se os usuários têm as permissões para agir de acordo com suas funções. 


### Tarefa 1: atribuir uma função de Administrador no Centro de Administração do Microsoft 365

A Holly Dickson recebeu a função de Administradora Global do Microsoft 365. Conforme você continua representando seu papel de Holly, você irá utilizar o Centro de administração do Microsoft 365 para atribuir direitos de administrador a um dos usuários da Adatum. Nesta tarefa, você irá atribuir a função Administrador de Cobrança à conta de usuário de Diego Siciliani.

1. Você concluiu o exercício de laboratório anterior trabalhando no LON-DC1. Agora você deve voltar para o **LON-CL1** para realizar as tarefas administrativas do Microsoft 365 neste exercício de laboratório. Como uma melhor prática, as tarefas administrativas típicas do Microsoft 365 devem ser realizadas em um PC cliente, em vez de no controlador de domínio da empresa.  <br/>

    Alterne para **LON-CL1**. 

2. No **LON-CL1**, no **Centro de administração do Microsoft 365** em seu navegador Edge, você deve continuar conectado como Holly Dickson do exercício de laboratório anterior. No painel de navegação, selecione **Usuários** e, em seguida, **Usuários Ativos**. 

3. Na lista de **Usuários ativos**, selecione **Diego Siciliani**.  <br/>

    **Observação:** Selecione o nome de Diego. Não marque a caixa de seleção à esquerda de seu nome. A caixa de seleção é normalmente usada para selecionar vários usuários quando você deseja realizar uma das ações relacionadas ao usuário na barra de menu que aparece acima da lista de usuários, como **Gerenciar licenças de produto** e **Gerenciar funções**. Selecionar o nome de um usuário abre um painel de propriedades específico para esse usuário.

4. No painel de **Diego Siciliani** que aparece, a guia **Conta** é exibida por padrão. Nesta guia, role para baixo até a seção **Funções** e selecione **Gerenciar funções**. 

5. Na janela **Gerenciar funções de administrador**, a opção **Usuário (sem acesso ao Centro de administração)** está atualmente selecionada por padrão. Agora que você deseja atribuir a Diego uma função de administrador, selecione a opção **Acesso ao Centro de administração**. Isso habilita uma lista de funções de administrador comumente usadas para seleção. 

6. Diego foi promovido a Administrador de Cobrança, mas como essa função não aparece na lista de funções comumente usadas, role para baixo e selecione **Mostrar todas por categoria**. 

7. Na lista de funções que estão ordenadas por categoria, role para baixo até a categoria **Outras**, marque a caixa de seleção **Administrador de Cobrança** e depois selecione **Salvar alterações**. <br/>

    **Dica:** Observe a mensagem que aparece na parte superior do painel assim que a alteração da função de administrador é salva. Essa mensagem fornece a melhor prática recomendada a seguir, que você deve ter em mente ao manter funções administrativas em suas implementações do mundo real: **Forneça aos usuários somente o acesso necessário atribuindo a função com as permissões mínimas possíveis**.

8. Na janela **Gerenciar funções de administrador**, selecione o **X** no canto superior direito da tela para fechá-la. Isso leva você de volta à lista de **Usuários ativos**. 

9. Permaneça conectado ao LON-CL1 e ao Centro de administração do Microsoft 365 como Holly Dickson.

### Tarefa 2: atribuir uma função de administrador usando um grupo de funções no Centro de administração do Microsoft 365

Na tarefa anterior, você atribuiu uma função de administrador diretamente à conta de usuário de Diego Siciliani no Centro de administração do Microsoft 365. Nesta tarefa, você irá atribuir funções usando um grupo de funções. Você irá criar um grupo de funções de segurança, depois irá atribuir funções de gerenciamento de usuários a esse grupo e, em seguida, irá atribuir o grupo de funções à conta de usuário de Lynne Robbin no Centro de administração do Microsoft 365.

1. No LON-CL1, você deve continuar conectado ao Centro de administração do Microsoft 365 como Holly Dickson. Caso não esteja, conecte-se agora.

2. No **Centro de administração do Microsoft 365**, selecione **Equipes e grupos** no painel de navegação e, em seguida, selecione **Equipes e grupos ativos**. 

3. Na página de **Equipes e grupos ativos**, a guia **Equipes e grupos do Microsoft 365** é exibida por padrão. Selecione a guia **Grupos de segurança**.

4. Na guia **Grupos de segurança**, selecione **+ Adicionar um grupo de segurança** na barra de menu. Ao fazer isso, inicia-se o assistente **Adicionar um grupo de segurança**.

5. No assistente **Adicionar um grupo de segurança**, na página **Configurar o básico**, digite **Grupo de funções de gerenciamento de usuários** no campo **Nome**. Digite **Este grupo de funções contém funções de gerenciamento de usuários** no campo **Descrição**. Selecione **Avançar**.

6. Na página **Editar configurações**, marque a caixa de seleção **As funções do Azure AD podem ser atribuídas ao grupo** e, em seguida, selecione **Avançar**.

7. Na página **Revisar e concluir a adição do grupo**, revise as configurações. Se alguma configuração precisar ser alterada, selecione a opção **Editar** apropriada e faça a alteração. Quando todas as configurações estiverem corretas, selecione **Criar grupo**.

8. Assim que o **Grupo de funções de gerenciamento de usuários** for criado, selecione **Fechar**.

9. Agora que você criou o grupo de funções, deve atribuir as funções correspondentes a ele. Na página **Equipes e grupos ativos**, a guia **Grupos de segurança** é exibida. Selecione o **Grupo de funções de gerenciamento de usuários** para abrir o painel de detalhes.

10. No painel do **Grupo de funções de gerenciamento de usuários**, a guia **Geral** é exibida por padrão. Na seção **Funções**, selecione **Gerenciar funções**.

11. No painel **Gerenciar funções de administrador** que aparece, selecione a opção **Acesso ao Centro de administração**. Na lista de funções comuns de administrador que aparece diretamente abaixo desta opção, marque as caixas de seleção **Administrador de Usuários** e **Gerente de Sucesso da Experiência do Usuário**. Em seguida, selecione a opção **Mostrar todas por categoria**. Role até a categoria **Identidade**. Observe como a função **Administrador de Usuários** já está selecionada, pois você a selecionou anteriormente na lista de funções comumente usadas. Nesta categoria de **Identidade**, selecione a função **Administrador de Assistência Técnica** e depois selecione **Salvar alterações**. 

12. No painel **Gerenciar funções de administrador**, as três funções selecionadas devem aparecer sob a opção **Acesso ao Centro de administração**. Selecione o **X** no canto superior direito do painel para fechá-lo.

13. Na guia **Grupos de segurança**, selecione **Grupo de funções de gerenciamento de usuários**. No painel **Grupo de funções de gerenciamento de usuários** que aparece, verifique se as três funções aparecem na seção **Funções**. Feche esse painel.

14. Agora que você atribuiu as funções ao grupo de funções, deve atribuí-lo à conta de usuário de Lynne Robbin. No **Centro de administração do Microsoft 365**, selecione **Usuários ativos**.

15. Na página **Usuários Ativos**, selecione **Lynne Robbins**. 

16. No painel **Lynne Robbins** que aparece, a guia **Conta** é exibida por padrão. Na tarefa anterior, quando você atribuiu a função de Administrador de Cobrança à conta de Diego Siciliani, você selecionou a opção **Gerenciar funções** na seção **Funções**. No entanto, como você irá atribuir as funções de Lynne através de um grupo de funções, deverá atribuir Lynne como membro do grupo de funções de segurança que acabou de criar. É através da atribuição ao grupo que Lynne irá herdar as funções atribuídas ao grupo de funções. Portanto, na seção **Grupos**, selecione **Gerenciar grupos**. 

17. No painel **Gerenciar grupos**, selecione **+Atribuir associações**.

18. No painel **Atribuir associações**, marque a caixa de seleção **Grupo de funções de gerenciamento de usuários** e, em seguida, selecione **Adicionar(1)**.

19. Assim que uma notificação de **Salvo** aparecer na parte superior da página, feche este painel. 

20. Para verificar se Lynne herdou as funções atribuídas ao grupo de funções de gerenciamento de usuários, selecione **Lynne Robbins** na lista de usuários ativos. 

21. No painel **Lynne Robbins** que aparece, na guia **Conta** que é exibida por padrão, você deve ver as três funções de gerenciamento de usuário que foram atribuídas a Lynne. Na seção **Funções**, selecione **Gerenciar funções**.

22. No painel **Gerenciar funções de administrador** que aparece, sob a opção **Acesso ao Centro de administração**, observe as três funções que estão selecionadas e o nome do grupo do qual elas foram atribuídas a Lynne. Também observe como as três funções estão esmaecidas. Isso indica que você não pode desmarcar as funções desta janela. Como as funções foram atribuídas a Lynne a partir de um grupo que continha essas funções, você só pode cancelar a atribuição removendo Lynne como membro do grupo de funções. Você acabou de verificar que Lynne recebeu essas funções. Feche este painel de **Gerenciar funções de administrador**.

23. Permaneça conectado ao LON-CL1 e ao Centro de administração do Microsoft 365 como Holly Dickson.

### Tarefa 3: atribuir uma função de administrador usando o Windows PowerShell  

Nesta tarefa, você irá usar o Windows PowerShell para atribuir uma função a uma conta de usuário. Ao fazer isso, você ganhará experiência em realizar essa função de gerenciamento no PowerShell, já que alguns administradores preferem realizar manutenções como essa usando o PowerShell.  

Nesta tarefa, Holly deseja atribuir a Patti Fernandez a função de Administradora do Suporte de Serviços. Para adicionar um usuário a uma função de administrador usando o módulo do Microsoft Graph PowerShell, você primeiro precisa obter a ID do objeto do usuário e a ID do objeto da função. Se a função ainda não foi habilitada (ou seja, não foi atribuída a um usuário ou não foi habilitada fisicamente), então você deve habilitar a função primeiro antes de poder atribuí-la a um usuário usando o PowerShell. Nesta tarefa, você irá habilitar a função de Administrador do Suporte de Serviços primeiro antes de atribuí-la a Patti Fernandez.

O PowerShell também permite exibir todos os usuários atribuídos a uma função específica, o que pode ser muito importante durante a auditoria de sua implantação do Microsoft 365. Nesta tarefa, você também irá aprender como usar o PowerShell para exibir todos os usuários atribuídos a uma função específica. 

1. No LON-CL1, selecione o ícone do Windows PowerShell na barra de tarefas que você deixou aberto do laboratório anterior. Se você fechou a janela do PowerShell, abra uma instância elevada dela usando a mesma instrução anterior. 

2. Sua sessão do PowerShell deve ainda estar conectada ao Microsoft Graph PowerShell do laboratório anterior, no qual você recuperou um grupo excluído usando o PowerShell. Mas se você fechou o PowerShell anteriormente e acabou de reabri-lo, importe o submódulo Microsoft.Graph.Identity.DirectoryManagement usando as mesmas etapas do exercício do laboratório anterior. 

3. Para realizar tarefas de manutenção de usuários do Microsoft 365 no Microsoft Graph PowerShell, você primeiro precisa importar o submódulo Microsoft.Graph.Users e solicitar permissões de Leitura/Gravação. Para importar este submódulo, digite o seguinte comando no prompt de comando e pressione Enter:   <br/>

        Import-Module Microsoft.Graph.Users

4. No exercício do laboratório anterior, você se conectou ao Microsoft Graph e solicitou permissões “Directory.ReadWrite.All” para executar os cmdlets que restauraram o grupo excluído. Para atualizar objetos de Usuário e Função nesta tarefa, Holly deve agora solicitar permissões de Leitura/Gravação para cada objeto. Para solicitar essas permissões, digite o seguinte comando no prompt de comando e pressione Enter:  <br/>

        Connect-MgGraph -Scopes 'User.ReadWrite.All', 'RoleManagement.ReadWrite.Directory'

5. Na janela **Escolha uma conta** que aparece, selecione a conta de Holly Dickson. 

6. Na caixa de diálogo **Permissões solicitadas** que aparece, marque a caixa de seleção **Consentir em nome da sua organização** e, em seguida, selecione **Aceitar**.

7. Holly deseja atribuir **Patti Fernandez** à função **Administrador do Suporte de Serviços**. Para atribuir esta função usando o Microsoft Graph PowerShell, você primeiro precisa obter a ID do objeto da função Administrador do Suporte de Serviços para que você possa atribuí-la a Patti. No entanto, no Microsoft Graph PowerShell, você só pode atribuir funções que foram “habilitadas”. Funções habilitadas são funções que foram habilitadas a partir de um modelo de função ou que já foram atribuídas a usuários por meio do PowerShell ou do Centro de administração do Microsoft 365. <br/>

    **Importante:** Antes de realizar esta etapa, verifique se sua janela do PowerShell está em modo de tela cheia. O nome da função aparece na última coluna no lado direito da tela. Se a janela não estiver em modo de tela cheia, não verá o nome da função associado a cada ID do objeto. 

    Para exibir todas as funções habilitadas no Microsoft 365, digite o seguinte comando no prompt de comando e pressione Enter: <br/>
    
        Get-MgDirectoryRole    <br/>

    **Observação:** Este comando exibe as funções que foram habilitadas até agora no Microsoft 365. Se a função Administrador do Suporte de Serviços aparecesse nesta lista, você poderia prosseguir diretamente para a etapa 13 para atribuir a função a Patti. No entanto, como Administrador do Suporte de Serviços não está incluído nesta lista de funções habilitadas, você deve realizar as etapas de 8 a 12 para habilitar a função a partir de seu modelo de função correspondente antes de poder atribuir Patti à ela na etapa 13. 

8. Para habilitar uma função no Microsoft Graph PowerShell, você primeiro deve localizar seu modelo para obter a ID do objeto do modelo. Você precisa saber a ID do objeto do modelo para habilitar a função a partir do modelo. Existem duas maneiras de exibir os modelos de função: você pode exibir a lista inteira de modelos de função ou pode exibir o modelo para uma função específica. Como uma experiência de aprendizado, você irá realizar ambos os métodos para que possa ver a diferença. <br/>

    Vamos começar exibindo a lista completa de modelos de função juntamente com suas IDs de objeto e nomes de exibição. Para fazer isso, digite o seguinte comando e pressione Enter: <br/>

        Get-MgDirectoryRoleTemplate | Format-List Id, DisplayName   <br/>

    Como você pode ver após ter executado este comando, você precisa rolar pela lista de modelos de função procurando pela função Administrador do Suporte de Serviços. É fácil perceber como isso pode ser entediante. Como alternativa, execute o seguinte comando para consultar um modelo de função específico, neste caso, o modelo de função “Administrador do Suporte de Serviços”: <br/>

        Get-MgDirectoryRoleTemplate | ? DisplayName -eq "Service Support Administrator"   <br/>

    Após executar este comando, você pode ver que ele exibe apenas o modelo de função solicitado. Obviamente, pode haver momentos em que exibir a lista completa de modelos de função seja necessário. Mas quando você precisa procurar um único modelo de função, executar o segundo comando do PowerShell será muito mais eficiente do que ter que rolar pela lista completa de modelos.
    
9. Agora que você consultou o modelo de função Administrador do Suporte de Serviços na etapa anterior, destaque sua **ID** (por exemplo, fe930be7-5e62-47db-91af-98c3a49a38b1) e pressione **Ctrl+C** para copiá-lo para a área de transferência (quando você o copia, o destaque desaparece).

10. Agora você irá criar uma variável que captura os atributos para o modelo de Administrador do Suporte de Serviços. Ao digitar o seguinte comando, pressione **Ctrl+V** para colar a ID do modelo de Administrador do Suporte de Serviços que você copiou para a área de transferência na etapa anterior. <br/>

    No prompt do comando, digite o seguinte comando e pressione Enter: <br/>

        $ServiceSupportRoleTemplate = @{ RoleTemplateID = "paste in template ID here" }  <br/>

    Por exemplo: $ServiceSupportRoleTemplate = @{ RoleTemplateID = "fe930be7-5e62-47db-91af-98c3a49a38b1" }

11. Agora você está pronto para habilitar a função de Administrador do Suporte de Serviços com base nos atributos do modelo que você capturou na variável $ServiceSupportRoleTemplate. Digite o comando a seguir e pressione Enter:  <br/>

        New-MgDirectoryRole -BodyParameter $ServiceSupportRoleTemplate

12. Para verificar se a função Administrador do Suporte de Serviços foi habilitada, digite o seguinte comando e pressione Enter. Este comando irá exibir a lista de funções habilitadas:  <br/>
            
        Get-MgDirectoryRole <br/>

    **Observação:** Este comando exibe a ID do objeto de todas as funções habilitadas, incluindo a função Administrador do Suporte de Serviços que você acabou de habilitar a partir de seu modelo. Posteriormente, você irá copiar e colar a ID do objeto da função Administrador do Suporte de Serviços na etapa 15 ao atribuir Patti a essa função.

13. Para atribuir Patti Fernandez à recém-habilitada função Administrador do Suporte de Serviços, você primeiro precisa obter a ID do objeto para a conta de usuário de Patti. Para fazer isso, digite o seguinte comando e pressione Enter: <br/>

        Get-MgUser | Format-List ID, DisplayName

14. Agora que você conhece a ID do objeto da função Administrador do Suporte de Serviços recém-habilitada e a ID do objeto da conta de usuário de Patti, você pode atribuir a função a Patti. Execute as seguintes etapas para concluir este processo: <br/>

    a. No comando anterior, você exibiu a lista de usuários ativos. Destaque a **ID** da conta de Patti e copie-a (**Ctrl+C**) para a área de transferência. O destaque desaparece assim que é copiado para a área de transferência.  <br/>

    b. Execute o seguinte comando que cria uma variável contendo o objeto de diretório para a conta de usuário de Patti. Ao digitar este comando, cole (**Ctrl+V**) a ID que você acabou de copiar para a conta de usuário de Patti. <br/>

        $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/paste in Patti's user account ID here" }  <br/>

    Por exemplo: $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/22fddbf7-42d2-4698-be65-ebc972a023e3" }

    c. Na etapa 12, você exibiu a lista de funções habilitadas. Destaque a ID da função Administrador do Suporte de Serviços e copie-a (**Ctrl+C**) para a área de transferência. <br/>

    d. Execute o comando a seguir que atribui a variável contendo a conta de usuário de Patti ($UserObject) à função do diretório. Ao digitar este comando, cole (**Ctrl+V**) a ID que você acabou de copiar para a função Administrador do Suporte de Serviços. <br/> 

        New-MgDirectoryRoleMemberByRef -DirectoryRoleId 'paste in the ID of the role here' -BodyParameter $UserObject
                
15. Agora você quer verificar se Patti foi atribuída à função de Administrador do Suporte de Serviços. Você copiou anteriormente a ID do objeto desta função para a área de transferência, e você a colou no comando anterior. Você também deve colá-la neste comando. Digite o seguinte comando e pressione Enter:
    
        Get-MgDirectoryRoleMember -DirectoryRoleId 'paste in the ID of the role here' 
                
16. O comando anterior apenas exibe as IDs dos usuários atribuídos à função selecionada. No entanto, você pode comparar a ID que é exibida com a ID de Patti para verificar se a conta dela foi atribuída à função **Administrador do Suporte de Serviços**. Como você pode ver, Patti é a única usuária atribuída à função. 

17. Agora vamos repetir esse processo para ver todos os usuários atribuídos à função de Administrador Global. Repita a etapa 15 para verificar quantos usuários da Adatum foram atribuídos à função de **Administrador Global**. Para completar este comando, você deve primeiro copiar (**Ctrl+C**) a ID da função Administrador Global para a área de transferência. Você pode encontrar essa ID na lista de funções habilitadas quando executou a etapa 12. <br/>

    **Aviso**: Copie a ID da função Administrador Global e NÃO a ID do modelo da função Administrador Global.

18. Verifique se há vários usuários da Adatum que foram atribuídos à função Administrador Global. Em um cenário do mundo real, o administrador do Microsoft 365 usaria este comando do PowerShell para monitorar quantos administradores globais existem em sua implantação do Microsoft 365. Eles então removeriam a função Administrador Global de qualquer usuário que realmente não deveria tê-la (lembre-se, a diretriz de melhor prática é ter entre 2 a 4 administradores globais em uma implantação do Microsoft 365, dependendo do tamanho da organização).  <br/>

    No caso deste laboratório, embora o provedor de hospedagem do seu laboratório tenha atribuído a função Administrador Global a usuários que não o administrador do MOD (e você atribuiu a Holly Dickson), você deixará esses usuários como estão. Nesta implantação fictícia da Adatum, não vale a pena perder tempo removendo essa função de suas contas. Além disso, algumas das futuras tarefas de laboratório são baseadas nesses usuários estarem atribuídos à função de Administrador Global. <br/>

    **IMPORTANTE:** Lembre-se de que em sua implantação do mundo real, o administrador do Microsoft 365 deve monitorar a função Administrador Global periodicamente para manter o número de usuários atribuídos entre 2 e 4.
    
19. Deixe sua sessão do Windows PowerShell aberta para os próximos exercícios de laboratório, mas minimize-a antes de prosseguir para a próxima tarefa.


### Tarefa 4: validar atribuições de função 

Nesta tarefa, você irá começar examinando as propriedades administrativas de dois usuários, Joni Sherman e Lynne Robbins. Em seguida, você irá entrar na página inicial do Microsoft 365 na VM Client 2 (LON-CL2) como cada usuário para confirmar várias das alterações que você fez ao gerenciar sua delegação administrativa nas tarefas anteriores. Por fim, como Lynne Robbins, você irá realizar duas tarefas importantes de manutenção de contas de usuário: redefinir senhas e bloquear contas de usuário.

1. No LON-CL1, você deve continuar conectado ao Centro de administração do Microsoft 365 como Holly Dickson. Caso não esteja, conecte-se agora.

2. No **Centro de administração do Microsoft 365**, se você não estiver visualizando os **Usuários Ativos**, então navegue até essa página agora.  

3. Na lista de **Usuários ativos**, selecione **Joni Sherman**. 

4. Na janela de propriedades de **Joni Sherman**, a guia **Conta** é exibida por padrão. Na seção **Funções**, ela deve indicar que Joni está **Sem acesso de administrador**. Selecione o **X** no canto superior direito para fechar a janela de propriedades de Joni.

5. Na lista de **Usuários ativos**, selecione **Lynne Robbins**. 

6. Na janela de propriedades de **Lynne Robbins**, deve indicar que Lynne foi atribuída à função **Administrador de Usuários**. Feche a janela de propriedades de Lynne.

7. Alterne para a VM Client 2 (**LON-CL2**).

8. No **LON-CL2**, na tela de logon, faça logon como o usuário local **Admin** com a senha **Pa55w.rd**.

9. Se a janela **Redes** for exibida, selecione **Sim**.

10. Na barra de tarefas, selecione o ícone **Microsoft Edge**. Maximize a janela do navegador Edge, se necessário.

11. No navegador **Edge**, navegue até **https://portal.office.com**. 

12. Você começará entrando no Microsoft 365 como **Joni Sherman**. Na janela **Entrar**, insira **JoniS@xxxxxZZZZZZ.onmicrosoft.com** (no qual xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório). <br/>

    **Importante:** Seu provedor de hospedagem de laboratório atribuiu uma **senha administrativa** à conta do administrador do MOD, e você atribuiu essa mesma **senha administrativa** à conta de Holly Dickson quando a criou. No entanto, seu provedor de hospedagem de laboratório atribuiu uma **Senha de usuário** diferente para todas as outras contas de usuário predefinidas. A partir de agora, ao fazer login como qualquer usuário que não seja o Administrador do MOD ou Holly Dickson, você deverá inserir essa **Senha de usuário** e NÃO a **Senha administrativa**. <br/>

    Como você está fazendo login como Joni Sherman, digite essa **Senha de usuário** na janela **Digite a senha**. Se necessário, conclua o processo de login do MFA.

13. Na janela **Permanecer conectado?**, marque a caixa de seleção **Não mostrar isso novamente** e depois selecione **Sim**. Se aparecer uma janela **Salvar senha**, selecione **Nunca**.

14. Se aparecer uma caixa de diálogo **Bem-vindo ao Microsoft 365** no meio da página, selecione a seta para frente (>) duas vezes e, em seguida, a marca de seleção para fechá-la.

15. Se aparecer uma janela **Encontrar mais aplicativos**, selecione **X** no canto superior da janela para fechá-la.

16. Na janela **Bem-vindo ao Microsoft 365**, que é a página inicial do Microsoft 365 de Joni, um painel de navegação aparece no lado esquerdo da tela que indica os aplicativos aos quais o usuário tem permissão de acesso. Neste painel **Aplicativos**, observe como a opção **Admin** não é exibida. Isso ocorre porque Joni nunca recebeu uma função de administrador do Microsoft 365. 

17. Agora você sairá do Microsoft 365 como Joni. No **Microsoft Edge**, no canto superior direito da página **Bem-vindo(a) ao Microsoft 365**, selecione o ícone do usuário para **Joni Sherman** (o círculo no canto superior com a foto de Joni) e, na janela **Joni Sherman** que aparecerá, selecione **Sair.** 

18. Agora você irá entrar no Microsoft 365 como **Lynne Robbins**. Na guia atual do navegador **Edge**, deve ser exibida uma mensagem indicando **Joni, você está desconectado agora**. Nesta janela, você tem a opção de entrar novamente como Joni ou entrar como um usuário diferente. <br/>

    Selecione **Alternar para uma conta diferente**, e no campo **Endereço de email** que aparece, insira **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (no qual xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório) e então selecione **Entrar**. Na janela **Digite a senha**, digite a **Senha do usuário** fornecida pelo seu provedor de hospedagem de laboratório e selecione **Entrar**. Se necessário, conclua o processo de login do MFA. 

19. Se aparecer uma caixa de diálogo **Bem-vindo ao Microsoft 365**, selecione a seta para frente (>) duas vezes e, em seguida, a marca de seleção para fechá-la.

20. Se aparecer uma janela **Encontrar mais aplicativos**, selecione **X** no canto superior da janela para fechá-la.

21. Na janela **Bem-vindo ao Microsoft 365**, que é a página inicial do Microsoft 365 de Lynne, observe como o ícone **Admin** é exibido no painel de navegação no lado esquerdo da tela. Esse ícone aparece porque Lynne foi atribuída a uma função de administrador do Microsoft 365. Selecione o ícone **Admin** para abrir o Centro de administração do Microsoft 365.

22. No **Centro de administração do Microsoft 365**, selecione **Usuários** no painel de navegação e depois selecione **Usuários ativos**. 

23. Como **Administradora de Usuários**, Lynne tem permissão para alterar as senhas dos usuários. Lynne foi recentemente contatada por **Diego Siciliani** e **Pradeep Gupta**, que relataram que suas senhas podem ter sido comprometidas. Conforme a política da empresa Adatum, Lynne deve redefinir suas senhas para um valor temporário e, em seguida, obrigá-los a redefinir sua senha no próximo logon.   <br/>

    Na lista de **Usuários ativos**, ao mover o mouse de uma conta de usuário para outra, observe o ícone de **chave (Redefinir uma senha)** que aparece à direita do nome de cada usuário. Selecione o ícone de chave que aparece à direita do nome de **Diego Siciliani**.

24. Na janela **Redefinir senha** para Diego, se a caixa de seleção **Criar automaticamente uma senha** exibir um marca de seleção, então selecione esta caixa para desmarcá-la. Isso permitirá que Lynne atribua manualmente a Diego uma senha temporária.  

25. Insira **Diego** no campo **Senha**. Observe à direita da senha, o sistema exibe uma mensagem indicando que esta é uma senha **Fraca**. Também observe a mensagem que aparece abaixo do campo indicando os requisitos para uma senha forte. Por último, observe como o botão **Redefinir senha** na parte inferior do painel não está habilitado. **Esse botão só será habilitado quando você inserir uma senha forte**.  

26. Verifique se a caixa de seleção **Exigir que este usuário altere a senha quando entrar pela primeira vez** está marcada (se não estiver, então selecione-a agora para mostrar uma marca de seleção). Insira **Pa55w.rd** no campo **Senha**. Observe que o campo **Senha** indica que essa é uma senha Forte. <br/>

    No entanto, agora marque a caixa de seleção **Exigir que este usuário altere a senha quando entrar pela primeira vez** para desmarcá-la. Observe que a mensagem de erro que aparece indicando a senha (Pa55w.rd) contém uma palavra, frase ou série de números que a torna facilmente previsível. Nesse caso, você inseriu uma variação da palavra **password** (ou “senha”, em português), que irá disparar esse erro. O sistema permite que você insira essa senha se forçar o usuário a alterá-la no primeiro acesso. Mas se você não forçar o usuário a inserir uma senha diferente no primeiro acesso, então esta senha não será permitida.

27. Após essas duas tentativas de senha fracassadas, Lynne decidiu permitir que o Microsoft 365 gere automaticamente uma senha. Marque a caixa de seleção **Criar automaticamente uma senha** para que ela exiba uma marca de seleção. <br/>
    
28. A senha que será gerada automaticamente será apenas uma senha temporária porque Lynne deseja forçar Diego a alterá-la na próxima vez que ele fizer logon. Portanto, verifique se a caixa de seleção **Exigir que este usuário altere a senha quando entrar pela primeira vez** exibe uma marca de seleção. Se a caixa estiver desmarcada, então selecione-a para que exiba uma marca de seleção.

29. Selecione **Redefinir senha**.

30. Se for solicitado para salvar a senha, selecione **Nunca** para fechar a janela.

31. Você deve receber uma mensagem de erro indicando que não é possível redefinir a senha de Diego porque ele foi atribuído a uma função de administrador. No caso de Diego, você atribuiu a ele a função Administrador de Cobrança anteriormente neste exercício prático. Como apenas os Administradores Globais podem alterar a senha de outro administrador, e como Lynne não é uma Administradora Global, ela terá que pedir a Holly Dickson para fazer essa alteração. Selecione **Fechar** no painel **Redefinir senha**. 

32. Se uma janela de solicitação de pesquisa aparecer, selecione **Cancelar**.

33. Na lista de **Usuários ativos**, selecione o ícone de **chave (Redefinir uma senha)** para **Pradeep Gupta**. 

34. Na janela **Redefinir senha** para Pradeep, verifique se a caixa de seleção **Criar automaticamente uma senha** exibe uma marca de seleção. Se não exibir, então selecione esta caixa agora para que o sistema gere automaticamente uma senha para Pradeep.  <br/>

    Esta é apenas uma senha temporária, pois Lynne quer forçar Pradeep a alterá-la na próxima vez que ele fizer logon. Portanto, verifique se a caixa de seleção **Exigir que este usuário altere a senha quando entrar pela primeira vez** exibe uma marca de seleção. Se a caixa estiver desmarcada, então selecione-a para que exiba uma marca de seleção.
    
35. Selecione o botão **Redefinir senha**.

36. Na janela **A senha foi redefinida**, você deve receber uma mensagem indicando que você redefiniu com sucesso a senha para Pradeep. Selecione **Fechar**.

37. A gerência descobriu recentemente que o nome de usuário de Alex Wilber pode ter sido comprometido. Consequentemente, Lynne foi solicitada a bloquear a conta de Alex para que ninguém possa entrar com seu nome de usuário até que a gerência consiga determinar a extensão do problema. Na lista de **Usuários ativos**, marque a caixa de seleção à esquerda do nome de **Alex Wilber** (NÃO selecione o nome de Alex).  <br/>

    **Importante:** Como você irá executar um comando global em vez de um comando associado à conta de Alex, você só quer a conta de Alex selecionada na lista de usuários ativos. Se alguma outra conta de usuário estiver selecionada, você deve desmarcar essa conta de usuário antes de prosseguir. Role para baixo na lista de usuários ativos e verifique se nenhuma outra conta de usuário está selecionada. Se outra conta que não seja a de Alex estiver selecionada, clique na caixa de seleção da conta para desmarcá-la. **Somente a conta de Alex Wilber deve estar selecionada.**

38. Na barra de menu superior da página, clique no **ícone de reticências (...)** para exibir um menu suspenso de ações adicionais. No menu exibido, selecione **Editar status de entrada**.

39. No painel **Bloquear entrada** que aparece, verifique se o endereço de email de Alex aparece abaixo do título **Bloquear entrada**. Marque a caixa de seleção **Bloquear a entrada deste usuário** e depois clique em **Salvar alterações**. 

40. A janela **Bloquear entrada** deve exibir uma mensagem indicando que Alex está agora bloqueado de fazer logon (e ninguém pode fazer logon com o nome de usuário de Alex no caso de seu nome de usuário ter sido realmente comprometido). Além disso, Alex será desconectado automaticamente dos serviços da Microsoft dentro de 60 minutos. Selecione **X** no canto superior do painel para fechá-lo. 

41. Lynne acabou de ser informada que o nome de usuário de **Nestor Wilke** também foi potencialmente comprometido. Para bloquear a capacidade de Nestor fazer logon (e impedir que qualquer outra pessoa use seu nome de usuário para fazer logon), repita as etapas de 33 a 36. <br/>

    Quando você tentou bloquear o logon de Nestor, deve ter recebido uma mensagem de erro indicando que **As alterações não puderam ser salvas**. A razão pela qual você recebeu esse erro é que Nestor é um Administrador Global, e Lynne não é. Somente um Administrador Global pode bloquear outro Administrador Global de fazer logon. Lynne precisará pedir a Holly Dickson para fazer essa mudança. <br/>

    Feche o painel **Boquear entrada**.

42. Você anteriormente bloqueou Alex Wilber de poder fazer logon. Para verificar se ele está bloqueado, você irá tentar fazer logon como Alex. Faça logoff do Microsoft 365 selecionando o ícone do usuário **Lynne Robbins** (o círculo com a foto de Lynne no canto superior) e, na janela **Lynne Robbins** que aparecerá, selecione **Sair.** 

43. Como melhor prática, feche todas as abas do seu navegador, exceto a aba **Sair**, depois de sair do serviço. Na guia **Sair**, navegue até **https://portal.office.com**. 

44. Na janela **Escolher uma conta**, selecione **Usar outra conta**. Na janela **Entrar**, insira **AlexW@xxxxxZZZZZZ.onmicrosoft.com** (no qual xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório). Na janela **Digite a senha**, digite a **Senha do usuário** fornecida pelo seu provedor de hospedagem do laboratório.  <br/>

    A janela **Escolher uma conta** deve aparecer e exibir uma mensagem de erro indicando que **Sua conta foi bloqueada. Entre em contato com sua equipe de suporte para desbloqueá-la e, em seguida, tente novamente. ** Você acabou de verificar que Alex (ou alguém que obteve o nome de usuário e senha de Alex) não pode fazer logon. <br/>

    **Observação:** Pode levar alguns minutos para que o bloqueio da conta seja completamente implementado. Até que o bloqueio seja implementado no sistema, Alex ainda pode conseguir fazer logon, mas nenhum dos serviços do Microsoft 365 estará disponível para ele, e eles não aparecerão no portal do Microsoft 365. Assim que uma conta for desbloqueada, os serviços estarão disponíveis novamente. <br/>

    Se você conseguir fazer logon como Alex, saia e aguarde alguns minutos. Este pode ser um bom momento para fazer uma pausa rápida. Então tente fazer logon novamente como Alex. Neste ponto, você deve esperar receber a mensagem de erro que indica que a conta de Alex foi bloqueada para fazer logon. 
    
45. Volte para **LON-CL1**. 

46. No **LON-CL1**, você deve continuar conectado ao **Microsoft 365** como Holly Dickson no seu navegador Edge. A lista de **Usuários ativos** deve ser exibida no **Centro de administração do Microsoft 365** conforme mencionado anteriormente nesta tarefa. 

47. Após uma investigação mais aprofundada, o CTO da Adatum determinou que a conta de Alex Wilber, de fato, não foi comprometida. Portanto, o CTO pediu a Holly que remova o bloqueio da conta de usuário de Alex. Repita as etapas de 33 a 36 para desbloquear a conta dele. Observe como a janela **Bloquear entrada** da etapa 35 agora exibe a janela **Desbloquear entrada** em vez disso.  <br/>

    Na janela **Desbloquear entrada**, a caixa de seleção **Bloquear a entrada deste usuário** está selecionada no momento. Desmarque esta caixa de seleção e, em seguida, selecione **Salvar alterações**. <br/>
    
    **IMPORTANTE:** Uma mensagem de aviso é exibida indicando que pode levar até 15 minutos antes que Alex possa fazer logon novamente. Devido às restrições de tempo com o treinamento, você **NÃO** irá tentar verificar se Alex pode fazer logon novamente. Se desejar, você pode tentar fazer logon como Alex em um momento posterior se estiver em pausa ou tiver tempo livre e quiser testar isso. Por enquanto, permaneça no LON-CL1 e simplesmente feche a janela **Desbloquear entrada**.
    
48. No LON-CL1, deixe seu navegador e todas as abas abertas e prossiga para o próximo exercício. 


# Fim do Laboratório 2

