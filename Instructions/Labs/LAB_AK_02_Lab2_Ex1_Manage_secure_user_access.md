# Roteiro de Aprendizagem 2, Laboratório 2, Exercício 1: Gerenciar o acesso seguro do usuário 

As organizações devem garantir que o acesso aos dados da empresa no Microsoft 365 esteja sempre seguro. O Microsoft 365 — e, por sua vez, o Copilot para Microsoft 365 — costuma mostrar dados sensíveis e confidenciais, incluindo emails, documentos, informações do cliente e propriedade intelectual. Um acesso não autorizado ao Microsoft 365 pode levar a violações de dados, roubo de identidade e outras atividades mal-intencionadas. Ao proteger o acesso do usuário, as organizações podem impedir que pessoas não autorizadas acessem e possivelmente façam um mau uso ou vazem dados da empresa ao trabalhar no Microsoft 365 e no Copilot para Microsoft 365.

No exercício de laboratório a seguir, você continuará representando seu papel de Holly Dickson,a nova Administradora do Microsoft 365 da Adatum. Você executará várias funções de gerenciamento de usuários para preparar a Adatum para sua futura implantação do Copilot para Microsoft 365. Você vai começar criando uma conta de usuário do Microsoft 365 para a Holly, que receberá a função de Administrador Global do Microsoft 365. 

**Observação:** O ambiente de VM fornecido pelo provedor de hospedagem do seu laboratório vem com mais de 20 contas de usuário do Microsoft 365 existentes, além de um grande número de contas de usuário locais existentes. Várias das contas de usuário do Microsoft 365 existentes serão usadas ao longo dos laboratórios neste curso. Embora a conta do Administrador MOD tenha sido criada pelo provedor de hospedagem do seu laboratório, você ainda precisará criar a conta de usuário para Holly Dickson, já que a boa prática é atribuir a função de Administrador Global do Microsoft 365 a mais de um usuário. Com isso, você também terá a experiência de criar uma conta de usuário do Microsoft 365, caso ainda não conheça o processo.

Holly foi então solicitada pelo CTO da Adatum para implantar a MFA (Autenticação Multifator do Microsoft Entra) e o Microsoft Entra Smart Lockout. Esses recursos ajudarão a fortalecer o gerenciamento de senhas em toda a organização em preparação para o Copilot para Microsoft 365. Para o Bloqueio Inteligente, você o implantará usando o Gerenciamento de Política de Grupo. 

**NOTIFICAÇÃO MFA IMPORTANTE:** Devido a uma alteração recente da Microsoft para os locatários de avaliação do Microsoft 365 usados neste curso, tivemos que fazer uma alteração correspondente neste laboratório. <br/>

**Design de laboratório original:** Este exercício de laboratório foi originalmente projetado para que, como Holly Dickson, você criou uma política de Acesso Condicional que habilitou a MFA no Adatum na Tarefa 3. Este é o método recomendado para habilitar a MFA, como você aprendeu na parte de palestra deste treinamento. Na tarefa 3, você criou uma política de Acesso Condicional que habilitou a MFA para todos os usuários, EXCETO para aqueles que eram membros do grupo de projetos piloto do Microsoft 365 que você criou em um exercício anterior. Para testar sua política na Tarefa 4, ela fez você fazer logon como adele Vance. Como Adele não era membro do grupo de projetos piloto, você tinha que concluir o processo de MFA para entrar no Microsoft 365. Você então saiu como Adele e entrou de volta como Holly Dickson. Como Holly é membro do grupo de projetos piloto do Microsoft 365, ela só tinha que inserir seu nome de usuário e senha. Ela não precisou executar uma segunda forma de autenticação usando a MFA. Essas duas etapas na Tarefa 4 verificaram sua política de Acesso Condicional – ou seja,  somente os usuários que não faziam parte do grupo de projetos piloto tinham que usar a MFA. 

A outra ramificação dessa política é que você não precisou usar a MFA ao entrar no restante dos laboratórios como os outros usuários de teste que também eram membros do grupo de projetos piloto do Microsoft 365. Embora as exclusões da MFA possam ser definidas por motivos práticos, dependendo das necessidades comerciais de uma empresa, as empresas devem avaliar cuidadosamente os riscos associados e aplicar exclusões com moderação, sempre visando se alinhar às práticas recomendadas de segurança. Este laboratório fez com que você criasse a exclusão do grupo de projetos piloto por dois motivos: para que você pudesse aprender a criar uma exclusão em uma política de Acesso Condicional, mas também como um meio de economizar tempo nos laboratórios de treinamento ao entrar como cada usuário de teste. <br/>

**Alteração do locatário da Microsoft:** Dito isto, a Microsoft criou desde então uma política de Acesso Condicional no locatário de avaliação do Microsoft 365 usado neste laboratório que requer MFA para todas as contas de usuário. Infelizmente, a política de Acesso Condicional da Microsoft tem precedência sobre a política de Acesso Condicional que você criará neste laboratório que exclui um grupo específico. As políticas de Acesso Condicional no Microsoft Entra são avaliadas em conjunto e a política de prioridade mais alta que se aplica a um usuário é imposta. Se houver várias políticas com a mesma prioridade, que é o caso aqui, a política mais restritiva se aplicará. Nesse caso, a política da Microsoft é mais restritiva do que a política que você cria, já que a sua inclui exceções de usuário. <br/>

**Impacto neste exercício de laboratório:** Embora a Microsoft imponha a MFA neste locatário de avaliação por meio de uma política de Acesso Condicional, você ainda criará sua própria política de Acesso Condicional, conforme originalmente projetado na Tarefa 3. A tarefa foi modificada ligeiramente de sua versão original para que você possa ver a política que a Microsoft construiu no locatário de avaliação. Mas, fora isso, a política que você criará não foi alterada em relação ao design original – ela requer MFA para todos os usuários, exceto para os membros do grupo de projetos piloto do Microsoft 365. No entanto, como a política que a Microsoft construiu no locatário de avaliação do laboratório é a mais restritiva das duas políticas, essa política tem precedência durante a imposição. Há duas implicações desse cenário. Primeiro, a política da Microsoft exige que você use a MFA ao entrar como cada usuário de teste pelo restante desses laboratórios. Em segundo lugar, como o Microsoft Entra ignorará sua política, não vale a pena testá-la. Dessa forma, removemos a Tarefa 4 original que testou a política de Acesso Condicional que você criou. Agora, mesmo que você não possa testar sua política, ainda queremos que você a crie na Tarefa 3 para que você obtenha essa experiência para suas implantações do mundo real. 

### Tarefa 1: Criar uma Conta de Usuário para o Administrador do Microsoft 365 da Adatum

Holly Dickson é a nova Administradora do Microsoft 365 da Adatum. Já que uma conta de usuário do Microsoft 365 ainda não foi configurada para ela, ela inicialmente entrou no Microsoft 365 com a conta do Administrador MOD (o administrador Global padrão) do laboratório anterior. Durante essa tarefa, em que você continuará conectado como o Administrador MOD, você criará uma conta de usuário do Microsoft 365 para a Holly. Você também atribuirá a função de Administrador Global do Microsoft 365 à conta da Holly. Essa função fornecerá a Holly as permissões necessárias para executar todas as funções administrativas no Microsoft 365. Após essa tarefa, você fará login usando a nova conta da Holly e executará todos os laboratórios restantes usando a persona da Holly. 

**Observação sobre a licença:** Antes de criar a conta da Holly, primeiro você irá verificará o número de licenças disponíveis. Ao fazê-lo, você irá perceber que, embora o locatário do seu laboratório forneça 20 licenças do Microsoft 365 E5 e 20 licenças do Enterprise Mobility + Security E5, todas essas licenças já foram atribuídas às contas de usuário existentes criadas pelo provedor de hospedagem do seu laboratório. Consequentemente, primeiro você precisará cancelar a atribuição de uma licença de cada tipo de um usuário existente para poder atribuí-la à Holly.

**Importante:** Uma boa prática para a sua implantação do mundo real é sempre anotar as credenciais da primeira conta de administrador Global (nesse laboratório, é a conta do Administrador MOD, cujo nome de usuário é admin@xxxxxZZZZZZ.onmicrosoft.com, em que xxxxxZZZZZZ é o prefixo de locatário atribuído pelo provedor de hospedagem do seu laboratório). Você deve guardar essas informações de conta em um lugar à parte por motivos de segurança. **Essa conta deve ser uma identidade NÃO personalizada** que possui os privilégios mais altos possíveis em um locatário. **Não** deve ser ativada por MFA porque não é personalizada. Como o nome de usuário e a senha dessa primeira conta de administrador Global costumam ser compartilhados entre vários usuários, essa conta é um alvo perfeito para os ataques e, portanto, é sempre recomendável que as organizações criem contas de administrador de serviço personalizadas (por exemplo, um administrador do Exchange, um administrador do SharePoint e assim por diante) e mantenham o menor número possível de administradores Globais pessoais. No caso dos administradores Globais pessoais que você cria em sua implantação do mundo real, cada um deles deve ser mapeado para um único usuário (como a Holly Dickson), e cada um deles deve ter a Autenticação Multifator (MFA) do Microsoft Entra implementada. Dito isto, a Microsoft já ativou a MFA por padrão para todos os usuários em seu locatário de avaliação do Microsoft 365.

1. Na VM **LON-CL1**, o **centro de administração do Microsoft 365** ainda deve estar aberto no navegador Microsoft Edge do exercício do laboratório anterior. Você precisa estar conectado no Microsoft 365 como o **Administrador MOD**. 

2. Já que você está adicionando um novo usuário, você deve começar verificando a disponibilidade de licença antes de adicionar a conta de usuário. No painel de navegação do **centro de administração do Microsoft 365**, selecione **Cobrança** para expandir o grupo Cobrança e, em seguida, selecione **Licenças**. 

3. Na página **Licenças**, a guia **Assinaturas** é exibida por padrão. Na lista de assinaturas, observe que as assinaturas **Enterprise Mobility + Security E5** e **Microsoft 365 E5** não têm licenças disponíveis. Seu locatário de laboratório fornece 20 licenças para cada assinatura, mas todas as 40 licenças foram atribuídas. Como você precisa atribuir à Holly tanto uma licença **Enterprise Mobility + Security E5** quanto uma licença do **Microsoft 365 E5**, primeiro você precisa cancelar a atribuição das licenças de uma conta de usuário existente para, em seguida, disponibilizá-las para a Holly. 

4. No painel de navegação do **centro de administração do Microsoft 365**, selecione **Usuários** e, em seguida, selecione **Usuários ativos**. Na lista **Usuários ativos**, você verá as contas de usuário existentes que foram criadas pelo provedor de hospedagem do seu laboratório. Como Christie Cline será transferida para uma nova função na empresa e não fará mais parte do projeto piloto do Microsoft 365, você irá cancelar a atribuição das licenças**Enterprise Mobility + Security E5** e **Microsoft 365 E5** da conta dela para que você possa reatribuí-las à nova conta da Holly Dickson.

5. Na página **Usuários Ativos**, na lista de usuários, selecione **Christie Cline** (selecione o nome de Christie com o hiperlink, não a caixa de seleção ao lado de nome dela).

6. No painel **Christie Cline** que aparece, a guia **Conta** é exibida por padrão. Selecione a guia **Licenças e aplicativos**. Em **Licenças (2)**, marque as caixas de seleção ao lado de **Enterprise Mobility + Security E5** e **Microsoft 365 E5** para desmarcá-las e selecione **Salvar alterações**. Após as alterações serem salvas, feche o painel **Christie Cline**. 

7. Agora está tudo pronto para você criar uma conta de usuário para Holly Dickson, que é a nova Administradora do Microsoft 365 da Adatum. Ao fazê-lo, você irá atribuir à Holly a função de Administrador Global do Microsoft 365, que fornece à Holly acesso global à maioria dos recursos de gerenciamento e dados nos serviços online da Microsoft. Você também atribuirá à Holly as duas licenças cuja atribuição à Christie Cline você acabou de cancelar. <br/>

    Na janela **Usuários Ativos**, selecione a opção **Adicionar um usuário** que aparece na barra de menus acima da lista de usuários ativos, para iniciar o assistente **Adicionar um usuário**.

8. Na página **Configurar o básico** do assistente **Adicionar um usuário**, insira as seguintes informações:

    - Nome: **Holly**

    - Sobrenome: **Dickson** 

    - Nome de exibição: Quando você acessa esse campo, o nome **Holly Dickson** vai aparecer.

    - Nome de usuário: **Holly** <br/>
    
        **IMPORTANTE:** À direita do campo **Nome de usuário** temos o campo do domínio, que estará preenchido previamente com o domínio de nuvem **xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório).<br/>
    
    - Limpe (desmarque) a caixa de seleção **Criar uma senha automaticamente**, que mostrará um novo campo para inserir uma senha definida pelo administrador.

    - No novo campo **Senha** que aparece, insira a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD)

    - Limpe (desmarque) a caixa de seleção **Exigir que esse usuário altere sua senha ao entrar pela primeira vez** 

9. Selecione **Avançar**. Se uma caixa de diálogo **Salvar senha** aparecer na parte superior da tela, selecione **Nunca**.

10. Na página **Atribuir licenças de produto**, insira as seguintes informações: <br/>

    - Selecione o local: **Estados Unidos**

    - Licenças: Na opção **Atribuir uma licença de produto ao usuário**, marque as caixas de seleção **Enterprise Mobility + Security E5** e **Microsoft 365 E5**

11. Selecione **Avançar**.

12. Na página **Configurações opcionais**, selecione a seta suspensa à direita de **Funções**. 

13. Na seção **Funções**, selecione a opção **Acesso ao centro de administração**. Ao selecionar essa opção, as funções de administrador mais comumente usadas do Microsoft 365 estarão habilitadas abaixo dela.  <br/>

    **Observação:** Todas as funções de administrador serão exibidas se você selecionar a opção **Mostrar tudo por categoria**, que aparece após a última função mais comum. No caso da Holly, você não precisa ver todas as funções de administrador por categoria porque a Holly receberá a função de Administrador Global que aparece na lista de funções comumente usadas.

14. Marque a caixa de seleção **Administrador Global**. <br/>

    **Observação:** Uma mensagem de aviso será exibida indicando que a Adatum já tem 7 administradores globais. Em um ambiente normal, isso seria excessivo e não recomendado. Para os fins desse laboratório, o provedor de hospedagem do seu laboratório atribuiu a função de administrador Global ao Administrador MOD e a outras seis contas de usuário, algo que você não veria normalmente em uma implantação do mundo real. No entanto, para os fins desse laboratório no seu ambiente fictício do laboratório da Adatum, ignore essa mensagem. **Dito isto, uma diretriz de boa prática que você deve seguir é ter de dois a quatro Administradores Globais nas suas implantações do Microsoft 365 no mundo real.** 

15. Selecione **Avançar**.

16. Na janela **Revisar e concluir**, reveja suas seleções. Se alguma coisa precisar ser alterada, selecione o link **Editar** apropriado e faça as alterações necessárias. Caso contrário, se tudo estiver correto, selecione **Terminar de adicionar**. 

17. Na página **Holly Dickson adicionada aos usuários ativos**, na seção **Detalhes do usuário**, selecione a opção **Mostrar** para verificar se a senha da Holly é a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD).  <br/>

    **Observação:** Se você inseriu uma senha diferente acidentalmente, depois de retornar à página **Usuários Ativos** você precisará selecionar o ícone **Redefinir uma senha** (o ícone de chave que aparece quando você passa o mouse sobre a conta da Holly) para alterar a senha dela para o valor correto.

18. Selecione **Fechar**.

19. Permaneça conectado à VM do Cliente 1 (LON-CL1) com o centro de administração do Microsoft 365 aberto no navegador para a próxima tarefa.

### Tarefa 2 – Adicionar Holly ao grupo de projetos piloto do Microsoft 365

Após concluir a tarefa anterior, você ainda deverá estar conectado ao **centro de administração do Microsoft 365** como a conta do **Administrador MOD**. Nessa tarefa, você começará a implementar o projeto piloto do Microsoft 365 da Adatum no papel de Holly Dickson, a nova Administradora do Microsoft 365 da Adatum. Portanto, você começará essa tarefa fazendo logon no Microsoft 365 como administrador MOD e fará logon novamente como Holly. 

Em uma tarefa anterior, você criou um grupo do Microsoft 365 para os membros da equipe de projeto piloto do Adatum para que você pudesse criar um tema personalizado para esse grupo. Nesta tarefa, você adicionará Holly a este grupo. 

1. Na VM LON-CL1, o **centro de administração do Microsoft 365** ainda deve estar aberto no navegador Microsoft Edge da tarefa anterior. Você precisa estar conectado no Microsoft 365 como o **Administrador MOD**. <br/>

    Na guia **centro de administração do Microsoft 365**, no canto superior direito da tela, observe que aparece o nome do Administrador MOD e um ícone de megafone. O nome é exibido devido ao tema personalizado que você criou no exercício de laboratório anterior, associado a um grupo de usuários do projeto piloto do Microsoft 365 que incluía o Administrador MOD. Tenha isso em mente quando fizer login como Holly Dickson. <br/>

    Selecione o ícone de usuário para o **Administrador MOD** no canto superior direito do seu navegador. Na janela **Administrador MOD** que aparece, selecione **Sair**. <br/>
    
    **Importante:** Ao sair de uma conta de usuário e entrar com outra, você deve fechar todas as guias do seu navegador, exceto a guia **Sair**. Essa é uma boa prática que ajuda a evitar qualquer confusão ao fechar as janelas associadas ao usuário anterior. Após sair da conta do Administrador MOD, reserve um momento para fechar todas as outras guias do navegador, exceto a guia **Sair**. 
    
2. No seu navegador Microsoft Edge, na guia **Sair**, insira a seguinte URL na barra de endereços para entrar novamente no Microsoft 365: **https://portal.office.com**. 

3. Na janela **Escolher uma conta**, aparece somente a conta de administrador de locatário do Administrador MOD (a conta de admin@xxxxxZZZZZZ.onmicrosoft.com) da qual você acabou de sair. Selecione **Usar outra conta**. 

4. Na janela **Entrar**, insira **Holly@xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório). Selecione **Avançar**.

5. Na janela **Inserir senha**, insira a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD) que você também atribuiu à conta de Holly e selecione **Entrar**. Se necessário, conclua o processo de login do MFA.  <br/>

    **Observação:** Desse ponto em diante, Holly e o administrador do MOD serão os únicos usuários que receberão a **Senha Administrativa** fornecida pelo provedor de hospedagem de laboratório. Todos os outros usuários recebem a **Senha de Usuário** fornecida pelo provedor de hospedagem de laboratório.

6. Se uma caixa de diálogo **Bem-vindo ao Microsoft 365** aparecer no meio da tela, não existirá uma opção para fechá-la. Em vez disso, à direita da janela, selecione o ícone de seta para a frente (**>**) duas vezes e, em seguida, selecione o ícone de marca de seleção para avançar pelos slides nessa janela de mensagens. 

7. Se uma janela **Criar com o Microsoft 365** aparecer, selecione o **X** no canto superior direito da janela para fechá-la. 

8. A página **Bem-vindo ao Microsoft 365** aparece no seu navegador Edge, na guia **Página Inicial | Microsoft 365**. Essa é a página inicial do Microsoft 365 da Holly. Observe que as iniciais de Holly aparecem no canto superior direito da tela; o nome de Holly, no entanto, não é exibido. Isso ocorre porque a conta da Holly não existia no momento em que você adicionou os usuários do projeto piloto do Microsoft 365 ao grupo associado ao tema personalizado no exercício de laboratório anterior. Já que a Holly quer ver seu nome na parte superior de cada janela do Microsoft 365 quando estiver conectada ao sistema, ela primeiro vai querer adicionar sua conta ao grupo de usuários do projeto piloto do Microsoft 365. <br>

    Na coluna de ícones de aplicativos que aparece no lado esquerdo da tela, selecione **Administrador**. Isso abre o **centro de administração do Microsoft 365** em uma nova guia do navegador. 

9. No **centro de administração do Microsoft 365**, selecione **Equipes e grupos** no painel de navegação e, em seguida, selecione no painel **Equipes e grupos ativos**. 

10. Na página **Equipes e grupos ativos**, temos uma guia para você conferir cada tipo de grupo. A guia **Equipes e Grupos do Microsoft 365** é exibida por padrão. Nessa guia, selecione **Projeto piloto do M365**.

11. No painel do **projeto piloto do M365** que aparece, a guia **Geral** é exibida por padrão. Selecione a guia **Filiação**.

12. Na guia **Filiação**, a subguia **Proprietários** é exibida por padrão no painel de navegação que aparece no lado esquerdo do painel. Selecione a subguia **Membros** que aparece abaixo dela.

13. Na sub-guia **Membros**, selecione **+Adicionar membros**.

14. No painel **Adicionar membros do grupo ao projeto piloto do M365** que aparece, selecione dentro do campo **Pesquisar por nome ou endereço de email**. Na lista de usuários que aparece, role para baixo e selecione **Holly Dickson**. Selecione o botão **Adicionar (1)** e, a seguir, feche o painel **Adicionar membros do grupo ao projeto piloto do M365** assim que a Holly for adicionada ao grupo.

15. Na página **Equipes e grupos ativos**, selecione o ícone **Atualizar** que aparece na parte superior da tela, à esquerda da barra de endereços. Observe como o nome de Holly Dickson aparece ao lado das iniciais no canto superior direito da tela (observação: você pode precisar atualizar duas vezes para ver o nome da Holly).

16. No **centro de administração do Microsoft 365**, selecione **Usuários** no painel de navegação e, em seguida, selecione **Usuários ativos**.

17. Na janela **Usuários Ativos**, quando você passa seu mouse sobre o **Nome de exibição** de um usuário um **ícone de chave** aparece à direita do nome do usuário. Ao selecionar o ícone de chave, você pode redefinir a senha de um usuário. Você precisa redefinir as senhas de Adele Vance, Alex Wilber, Joni Sherman, Lynne Robbins e Patti Fernandez para a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD) e que você anteriormente atribuiu a Holly Dickson.<br/>

    Passe o mouse sobre **Adele Vance** e selecione o ícone de chave que aparece.

18. No painel **Redefinir senha** que aparece para a Adele, limpe (desmarque) a caixa de seleção **Criar uma senha automaticamente**. 

19. No campo **Senha** que aparece, insira a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD). Selecione o ícone de olho (**Mostrar Senha**) na ponta do campo **Senha** para ver o valor que você inseriu. Verifique se você inseriu a senha do locatário corretamente.

20. Limpe (desmarque) a caixa de seleção **Exigir que esse usuário altere sua senha quando entrar pela primeira vez**.

21. Selecione **Redefinir Senha**. Se uma caixa de diálogo **Salvar senha** aparecer na parte superior da tela, selecione **Nunca**. Em seguida, selecione **Fechar** no painel **A senha foi redefinida**.

22. Repita as etapas 17-21 para **Alex Wilber**, **Joni Sherman**, **Lynne Robbins** e **Patti Fernandez**. Redefina cada uma das respectivas senhas para a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD). Na etapa 19, não se esqueça de exibir a senha que você inseriu para verificar se o valor está correto.

23. Permaneça conectado no LON-CL1 com o **centro de administração do Microsoft 365** aberto no seu navegador para a próxima tarefa.


### Tarefa 3: Implantar a MFA usando uma política de Acesso Condicional

Como seu treinamento indicou, existem três maneiras de implementar a MFA: com políticas de Acesso Condicional, com padrões de segurança e com a MFA por usuário herdada (não recomendada para organizações maiores). Nesse exercício, você vai habilitar a MFA por meio de uma política de Acesso Condicional, que é o método recomendado pela Microsoft. O Adatum orientou Holly a habilitar a MFA para todos os seus usuários do Microsoft 365 - internos e externos. No entanto, para testar a implementação do projeto piloto do Microsoft 365 da Adatum, a Holly quer isentar os membros do grupo do projeto piloto da M365 da exigência de usar MFA para entrar. Após o projeto piloto ter sido concluído, a Holly irá atualizar a política removendo a isenção da exigência de MFA desse grupo. A política também incluirá duas outras exigências. Exigirá a MFA para todos os aplicativos de nuvem e exigirá a MFA mesmo que um usuário faça login a partir de um local confiável. 

1. Na VM LON-CL1, o **centro de administração do Microsoft 365** ainda deve estar aberto no navegador Microsoft Edge da tarefa anterior. Você deve estar conectado ao Microsoft 365 como **Holly Dickson**.
   
2. No **centro de administração do Microsoft 365**, na seção **Centros de administração** no painel de navegação, selecione **Identidade**. Isso abre o centro de administração do Microsoft Entra em uma nova guia do navegador. Se uma janela **Escolher uma conta** for exibida, selecione **conta de Holly Dickson**.

3. No **centro de administração do Microsoft Entra**, selecione **Proteção** no painel de navegação e, a seguir, selecione **Acesso Condicional**.

4. Na página **Acesso Condicional | Visão geral**, selecione **Políticas** no painel de navegação do meio.

5. Na página **Acesso Condicional | Políticas**, leia as políticas padrão disponíveis com sua assinatura do Microsoft 365. Observe que a política intitulada **Autenticação multifator para parceiros e fornecedores da Microsoft**. Esta é a política de Acesso Condicional que a Microsoft criou que requer MFA para todos os usuários em todos os aplicativos de nuvem. Selecione essa política para que você possa ver como a Microsoft está impondo MFA para todos os usuários neste locatário de avaliação.

6. Na página **Autenticação multifator** para parceiros e fornecedores da Microsoft, no grupo **Usuários**, selecione **Todos os usuários incluídos e usuários específicos excluídos**. Fazer isso irá exibir duas guias: **Incluir** e **Isentar**.

7. Na guia **Incluir**, observe que **Todos os usuários** está selecionado. Só para satisfazer sua curiosidade, vamos tentar alterar essa política desativando a MFA. Selecione **Nenhum** e, em seguida, selecione o botão **Salvar**. <br/>

    **Observe o que aconteceu:** Uma caixa de mensagem apareceu brevemente na parte superior da página indicando **Falha ao atualizar a autenticação multifator para parceiros e fornecedores da Microsoft**. Em seguida, o sistema retornou você à página **Acesso Condicional | Políticas**. Se você não viu essa mensagem, repita esta etapa novamente.  <br/>

    O mesmo acontece se, na guia **Incluir**, você selecionar **Usuários e grupos** e selecionar usuários ou grupos específicos em vez de todos os usuários. Na verdade, a Microsoft criou um firewall de segurança para que, se você tentar fazer qualquer alteração nessa política, ela falhará quando você tentar salvar a política. 

8. A Microsoft compilou uma exclusão nessa política. Vamos dar uma olhada. Na página **Políticas**, selecione novamente a política **Autenticação multifator para parceiros e fornecedores da Microsoft** e, em seguida, selecione **Todos os usuários incluídos e usuários específicos excluídos**. Desta vez, selecione a guia **Excluir**. 

9. Observe que a Microsoft selecionou a caixa de seleção **funções de Diretório**. Selecione o campo abaixo dessa opção. No menu de funções que você pode optar por excluir da MFA, a única função selecionada pela Microsoft é **Contas de Sincronização de Diretório**. Essa função é atribuída automaticamente à conta de serviço do Microsoft Entra Connect Sync e não deve ser usada de outra forma. É uma função especial que tem permissões apenas para executar tarefas de sincronização de diretório. Essa função é crucial para sincronizar um AD DS (Active Directory Domain Services) local com a ID do Microsoft Entra, fornecendo coexistência de identidade. A Microsoft não requer MFA para essa função porque o serviço de sincronização precisa ser executado continuamente sem interrupções que possam ser causadas por prompts de MFA. Além disso, essa conta de serviço é configurada com permissões muito limitadas e não é usada para entradas interativas, o que reduz o risco de segurança.   <br/>

    Assim como na etapa anterior em que você tentou alterar a configuração de MFA para não incluir usuários ou usuários selecionados, se você tentar selecionar outras funções para contornar a configuração de MFA, terá o mesmo erro indicando **Falha ao atualizar a autenticação multifator para parceiros e fornecedores da Microsoft** ao tentar salvar a política. O firewall de segurança da Microsoft não permite nenhuma alteração nessa política de Acesso Condicional que afete aqueles que devem usar a MFA.

10. Se você ainda tiver a página **Autenticação multifator para parceiros e fornecedores da Microsoft** aberta, selecione o **X** no canto superior para fechá-la e voltar à página **Acesso Condicional | Políticas**. Ou, se você tentou salvar uma alteração na política, sua tentativa terá falhado e você já deverá estar de volta à página **Acesso Condicional | Políticas**.

11. Na página **Acesso condicional | Políticas**, na barra de menus na parte superior da página, selecione **+Nova política**.

12. Na janela **Nova Política de Acesso Condicional**, insira **MFA para todos os usuários do Microsoft 365** no campo **Nome**.

13. Você começará por definir a exigência de MFA para os usuários. No grupo **Usuários**, selecione **0 usuários e grupos selecionados**. Fazer isso irá exibir duas guias: **Incluir** e **Isentar**.

14. Na guia **Incluir**, selecione **Todos os usuários**. Observe a mensagem de aviso que aparece. Você abordará isso nas próximas duas etapas.

15. Selecione a guia **Isentar**. Para evitar o bloqueio do sistema, como a mensagem de aviso anterior indicou, você vai querer isentar seus administradores globais — nesse caso, a Holly. Durante os testes, a Holly também vai querer isentar os outros membros do grupo do projeto piloto do Microsoft 365, por uma questão de conveniência. Após o Microsoft 365 entrar em operação, a Holly irá remover o grupo do projeto piloto da lista de Isenções nessa política de Acesso Condicional e, simplesmente, excluirá a si mesma e vários outros administradores globais. Mas, por enquanto, a Holly quer isentar o grupo inteiro. <br/>

    Para fazê-lo, selecione **Usuários e grupos**. 

16. Na janela **Selecionar usuários e grupos isentos** que aparece, você vai querer selecionar o grupo do projeto piloto do Microsoft 365. A guia **Todos** é exibida por padrão. Para localizar o grupo do projeto piloto rapidamente, selecione a guia **Grupos**. Na lista de grupos ativos, marque a caixa de seleção ao lado do grupo **Projeto piloto do M365** e, em seguida, selecione o botão **Selecionar** na parte inferior da janela. De volta à janela **Nova Política de Acesso Condicional**, observe a mensagem que aparece na seção **Usuários**. 

17. Agora, você vai definir a exigência de MFA para todos os aplicativos de nuvem. Na seção **Recursos de destino**, selecione **Nenhum recurso de destino selecionado**. Fazer isso irá exibir duas guias: **Incluir** e **Isentar**.

18. Selecione o menu suspenso **Selecione a que se aplica essa política** para ver as várias opções no menu suspenso. Selecione **Aplicativos de nuvem**. 

19. Na guia **Incluir**, observe que a configuração padrão é **Nenhum**. Se você não alterou essa configuração, nenhum aplicativo de nuvem exigiria MFA - e isso inclui o Microsoft 365. Portanto, mesmo que você criasse essa política e selecionasse a opção de exigir MFA para todos os usuários, mas deixasse essa configuração de **Recursos de destino** como **Nenhum**, nenhum usuário que entrasse no Microsoft 365 precisaria usar a MFA. <br/>

    Na guia **Incluir**, selecione a opção **Selecionar aplicativos**. Isso exibe duas seções: **Editar filtro** e **Selecionar**. Na seção **Selecionar**, selecione **Nenhum**. No painel **Selecionar aplicativos de nuvem** que aparece, role para baixo ao longo da lista de aplicativos para ver todos os diferentes aplicativos para os quais você poderia exigir a MFA. **NÃO selecione nenhum dos aplicativos.** Estamos fazendo você percorrer essa lista apenas para ter uma ideia do nível de granularidade você pode obter ao exigir a MFA, caso decida limitar a MFA a determinados aplicativos.  <br/>

    No caso da Adatum, a Holly quer exigir a MFA para todos os aplicativos de nuvem, o que costuma ser um cenário corporativo mais comum do que selecionar aplicativos específicos. Na guia **Incluir**, selecione a opção **Todos os aplicativos de nuvem**. A Adatum não irá isentar nenhum aplicativo de nuvem da autenticação multifator (MFA). Você pode selecionar a guia **Excluir** se quiser ver as opções que ela fornece. Ele funciona basicamente da mesma forma que a guia **Incluir**. Você pode exibir essa guia, mas NÃO selecione nenhum aplicativo de nuvem para exclusão. 

20. Para terminar, você vai definir a exigência de MFA para todos os locais de login do usuário. Em alguns cenários, as organizações talvez só exijam a MFA se um usuário fizer login a partir de um local não confiável. No entanto, o Adatum deseja exigir MFA para todos os usuários incluídos, independentemente de onde eles se conectarem. <br/>

    Em **Condições**, selecione **0 condições selecionadas**. Fazer isso vai exibir uma lista de possíveis condições que a política irá verificar. Para esse exercício de laboratório, na condição **Locais**, selecione **Não configurados**. Fazer isso vai exibir um botão de alternância para **Configurar** e duas guias: **Incluir** e **Isentar**. Ambas as guias estão desabilitadas no momento.

21. Defina botão de alternância **Configurar** como **Sim**, o que habilita as duas guias. 

22. Na guia **Incluir**, verifique se **Qualquer local** está selecionado (você pode selecioná-lo, se necessário). Selecione a guia **Isentar**. Se a sua organização reconhecer endereços ou intervalos de endereços IP específicos como "confiáveis", você poderá excluir a exigência de MFA se um usuário fizer login a partir de um desses locais. No entanto, o Adatum deseja exigir MFA para todas as tentativas de entrada do usuário, independentemente de sua localização. Isso incluirá tanto os logins de usuários internos quanto externos. Verifique se a opção **Locais selecionados** está selecionada e, na seção **Selecionar**, verifique se **Nenhum** está selecionado. Ao especificar que nenhum local está selecionado, essa configuração garante que nenhum local fique isento da MFA. 

23. Na seção **Controles de acesso**, no grupo **Conceder**, selecione **0 controles selecionados**. Fazer isso irá exibir um painel **Conceder**.

24. No painel **Conceder** que aparece, verifique se a opção **Conceder acesso** está selecionada (você pode selecioná-la, se necessário). A seguir, marque a caixa de seleção **Exigir autenticação multifator**. Observe todos os outros controles de acesso disponíveis que podem ser habilitados com essa política. Para essa política, você só precisará da MFA. Selecione o botão **Selecionar** na parte inferior do painel **Conceder**, que fechará o painel. 

25. Na parte inferior da **Nova** janela, no campo **Habilitar política**, selecione **Habilitada**.

26. Observe a opção que aparece na parte inferior da página, alertando para você não se bloquear do lado de fora. Selecione a opção **Eu entendo que minha conta será afetada por essa política. Continuar assim mesmo.** Na verdade, a Holly não será afetada, já que faz parte do grupo do projeto piloto do M365, que é isento dessa política.

27. Selecione o botão **Criar** para criar a política.

28. Na janela **Acesso Condicional | Políticas** que aparece, verifique se a política **MFA para todos os usuários do Microsoft 365** aparece e se seu **Estado** está definido como **Habilitada**.

29. Permaneça conectado ao LON-CL1 com todas as guias do seu navegador Microsoft Edge abertas para a próxima tarefa.

**Observação:** De acordo com a discussão anterior, não há como testar sua política de Acesso Condicional no locatário de avaliação atual do Microsoft 365. A política de Acesso Condicional da Microsoft requer MFA para todos os usuários. Quando você tem várias políticas que exigem MFA, a política mais restritiva se aplica. Nesse caso, a política da Microsoft é mais restritiva do que a que você acabou de criar que incluiu exceções para os membros do grupo de projetos piloto. Mesmo que você não possa testar sua política usando esse locatário de avaliação, recomendamos que você use essa experiência de criação de uma política de Acesso Condicional para exigir MFA em suas implantações do Microsoft 365 no mundo real.


### Tarefa 4: Implantar o Bloqueio Inteligente do Microsoft Entra

O Diretor de Tecnologia da Adatum pediu para você implantar o Bloqueio Inteligente do Microsoft Entra, que ajuda a bloquear atores mal-intencionados que tentam adivinhar as senhas dos seus usuários ou usam métodos de força bruta para serem aceitos na sua rede. O Bloqueio Inteligente pode reconhecer os logins provenientes de usuários válidos e tratá-los diferentemente dos logins de invasores e outras origens desconhecidas. 

O Diretor de Tecnologia está ansioso para implementar o Bloqueio Inteligente porque o recurso bloqueará os invasores e, ao mesmo tempo, permitirá que os usuários da Adatum continuem a acessar suas contas e a ser produtivos. O Diretor de Tecnologia pediu à Holly para configurar o Bloqueio Inteligente para que os usuários não possam usar a mesma senha mais de uma vez, além de não poderem usar senhas consideradas muito simplistas ou muito comuns. 

**Observação:** você pode fazer a manutenção das configurações da Política de Bloqueio de Contas no Editor de Gerenciamento de Política de Grupo e no Microsoft Entra por meio do seu recurso de Bloqueio Inteligente. Essa tarefa do laboratório mostra como acessar cada método, mesmo considerando que você só irá atualizar as configurações do Bloqueio Inteligente no Microsoft Entra. Você precisa usar o controlador de domínio da empresa (LON-DC1) para acessar o Editor de Gerenciamento de Política de Grupo. 

1. Nas tarefas anteriores, você trabalhou no LON-CL1. Nessa tarefa, você estará trabalhando no controlador de domínio da Adatum, LON-DC1. <br/>

    Alterne para o **LON-DC1**.

2. No **LON-DC1**, você precisa selecionar **Ctrl+Alt+Delete** para fazer login (seu instrutor irá orientar você sobre o que fazer para encontrar essa opção no seu ambiente de VM). Faça login no LON-DC1 com a conta de administrador local da Adatum que foi criada pelo provedor de hospedagem do seu laboratório (**Administrador**) com a senha **Pa55w.rd**.

3. No LON-DC1, o **Gerenciador do Servidor** é iniciado automaticamente na inicialização. No **Gerenciador do Servidor**, selecione **Ferramentas** na barra de menus do canto superior direito e, no menu suspenso, selecione **Gerenciamento de Política de Grupo**. Maximize a janela **Gerenciamento de Política de Grupo** que aparece.

4. Você vai querer editar a política de grupo que inclui a política de bloqueio de conta da sua organização. Se necessário, na árvore do console raiz no painel do lado esquerdo, expanda **Forest:Adatum.com**, expanda **Domínios**e, a seguir, expanda **Adatum.com**.  <br/>

    Em **Adatum.com**, clique com o botão direito do mouse na **Política de Domínio Padrão** e selecione **Editar** no menu.

5. Maximize a janela **Editor de Gerenciamento de Política de Grupo** que aparece.

6. Na árvore **Política de Domínio Padrão** no painel do lado esquerdo, em **Configuração do Computador**, expanda **Políticas**, expanda **Configurações do Windows**, expanda **Configurações de Segurança** e, a seguir, expanda **Políticas de Conta**.

7. Na pasta **Políticas de Contas**, selecione **Política de Bloqueio de Contas**.

8. Como você pode ver no painel do lado direito, nenhum dos parâmetros do bloqueio inteligente foi definido. Em vez de fazer a manutenção desses parâmetros de bloqueio no Editor de Gerenciamento de Política de Grupo, você vai usar o centro de administração do Microsoft Entra. Embora você possa usar o Editor de Gerenciamento de Política de Grupo, esse método costuma ser mais usado em ambientes locais do Active Directory. Mostramos esse editor para que você pudesse ver essa alternativa. No entanto, para as organizações que usam estritamente serviços baseados em nuvem como o Microsoft 365, ou que acham que usar o centro de administração do Microsoft Entra é muito mais fácil do que acessar o Editor de Gerenciamento de Política de Grupo, pode ser preferível usar o **centro de administração do Microsoft Entra** para atribuir os valores correspondentes no contexto do Entra ID. <br/>  

    Lembre-se também de que o comportamento do bloqueio e as opções de personalização dos dois métodos são diferentes. Com o Editor de Gerenciamento de Política de Grupo, você tem um controle mais granular sobre as configurações das políticas, incluindo o Limite de Bloqueios de Conta, a Duração do Bloqueio e Redefinir o Contador do Bloqueio de Conta Após. No entanto, usar esse método requer familiaridade com Políticas de Grupo e a administração do Active Directory. A Política de Bloqueio de Contas no Microsoft Entra, por outro lado, não pode ser personalizada tão amplamente mas é mais fácil de usar, embora não tenha algumas das opções de ajuste fino disponíveis na Política de Grupo. <br/>

    No caso da Adatum, a Holly optou por usar o centro de administração do Microsoft Entra para configurar a política de Bloqueio de Contas da empresa. Na barra de tarefas na parte inferior da sua tela, selecione o ícone do **Microsoft Edge**. Se necessário, maximize a janela do seu navegador quando for aberta.

9. No seu navegador Edge, vá para a página inicial do **Microsoft 365** inserindo a seguinte URL na barra de endereços: **https://portal.office.com** 

10. Na caixa de diálogo **Entrar**, você precisa entrar como Holly Dickson. Insira **Holly@xxxxxZZZZZZ.onmicrosoft.com**, em que xxxxxZZZZZZ é o prefixo de locatário atribuído pelo provedor de hospedagem do seu laboratório. Selecione **Avançar**. <br/>

11. Na caixa de diálogo **Inserir senha**, insira a **Senha Administrativa** exclusiva fornecida pelo provedor de hospedagem do seu laboratório e, em seguida, selecione **Entrar**. Se necessário, conclua o processo de login do MFA.

12. Na caixa de diálogo **Permanecer conectado?** selecione a caixa de seleção **Não mostrar novamente** e, em seguida, selecione **Sim**. Na caixa de diálogo **Salvar senha** que aparece, selecione **Nunca**.

13. Se uma caixa de diálogo **Bem-vindo ao Microsoft 365** aparecer no meio da tela, não existirá uma opção para fechá-la. Em vez disso, à direita da janela, selecione o ícone de seta para a frente (**>**) duas vezes e, em seguida, selecione o ícone de marca de seleção para avançar pelos slides nessa janela de mensagens. 

14. Se uma janela **Localizar mais aplicativos** ou uma janela **Criar com o Microsoft 365** aparecerem, selecione o **X** no canto superior direito dessas janelas para fechá-las. 

15. Na página **Bem-vindo ao Microsoft 365**, na lista de ícones de aplicativos que aparece no painel do lado esquerdo, selecione **Administrador**; isso abrirá o **centro de administração do Microsoft 365** em uma nova guia do navegador. 

16. No **Centro de administração do Microsoft 365**, selecione **Mostrar tudo** no painel de navegação. Em **Centros de administração**, selecione **Identidade**, que mostrará o **centro de administração do Microsoft Entra** em uma nova guia.

17. No **centro de administração do Microsoft Entra**, selecione **Proteção** no painel de navegação e, a seguir, selecione **Métodos de autenticação**.

18. Na página **Métodos de Autenticação | Políticas**, no painel do meio, na seção **Gerenciar**, selecione **Proteção por senha**.

19. Na janela **Métodos de autenticação | Proteção de senha**, no painel de detalhes no lado direito, insira as seguintes informações:

    - Na seção **Bloqueio inteligente personalizado**:

        - **Limite de bloqueios:** esse campo indica quantos logins com falha são permitidos em uma conta antes de ser bloqueada pela primeira vez. O padrão é 10. Para fins de teste, a Adatum solicitou que você o definisse como **3**.

        - **Duração do bloqueio em segundos**: Essa é a duração em segundos de cada bloqueio. O padrão é 60 segundos (um minuto). A Adatum solicitou que você alterasse isso para **90** segundos.

    - Na seção **Senhas proibidas personalizadas**:

        - **Implementar lista personalizada**: selecione **Sim**

        - **Lista de senhas proibidas personalizadas:** Insira os seguintes valores (pressione Enter após inserir cada valor para que cada valor fique em uma linha separada):

            - **Password01**

            - **F00tball01**

            - **Se@Hawks1**

            - **Never4get!!**

    - Na seção **Modo**, selecione **Implementado**

20. Selecione **Salvar** na barra de menus na parte superior da página.

21. Agora, você deve testar a funcionalidade de senha proibida. Selecione o ícone de usuário da Holly Dickson no canto superior direito da tela e, no menu que aparece, selecione **Ver conta**. 

22. Na janela **Minha conta** que aparece, no bloco **Senha**, selecione **ALTERAR SENHA**.

23. Uma nova guia será aberta mostrando a janela **Alterar senha**. No campo **Senha antiga**, insira a senha existente de Holly, que é a mesma **Senha Administrativa** fornecida pelo provedor de hospedagem do seu laboratório para a conta de administrador do locatário (ou seja, a conta do Administrador MOD). <br/>

    Insira **Never4get!!** nos campos **Criar nova senha** e **Confirmar nova senha** e, em seguida, selecione **Enviar**. Observe a mensagem de erro que você receber.

24. No seu navegador, feche a guia **Alterar senha**. 

25. Agora você deve testar a funcionalidade do limite de bloqueios. Selecione o ícone de usuário da Holly Dickson no canto superior direito da tela e, no menu que aparece, selecione **Sair**.  

26. Após ter saído como Holly, a janela **Escolher uma conta** aparecerá na guia **Entrar no Microsoft Entra**. Como boa prática, ao sair de um serviço online da Microsoft como um usuário e entrar novamente como outro, feche todas as guias do seu navegador, exceto as guias **Sair** ou **Entrar**. Nesse caso, feche as outras guias agora e deixe a guia **Entrar** aberta.  <br/>

    Na janela **Escolher uma conta**, selecione **Usar outra conta**. 

27. Na janela **Entrar**, você vai fazer login como Patti Fernandez. Insira ****pattif@xxxxxZZZZZZ.onmicrosoft.com (em que xxxxxZZZZZZ é o prefixo de locatário atribuído a você pelo provedor de hospedagem do seu laboratório) e selecione **Avançar**. 

28. Na janela **Inserir senha**, insira qualquer combinação aleatória de letras e números e selecione **Entrar**. Observe a mensagem de erro de senha inválida que aparece. 

    Repita essa etapa mais duas vezes. 
    
    Já que definiu o **Limite de bloqueios** como **3**, você deve receber uma mensagem de erro indicando que essa conta está bloqueada após a terceira tentativa de login com falha. <br/>

    **Observação:** Se você não receber essa mensagem de bloqueio após a terceira tentativa, isso significa que o sistema ainda não terminou de propagar essa alteração do limite de bloqueios no serviço inteiro. Pode levar vários minutos para que as alterações entrem em vigor. Aguarde alguns minutos e entre novamente com uma senha falsa. Os testes desse laboratório têm apresentado resultados variados. Às vezes, a alteração é propagada quase imediatamente para que sua conta seja bloqueada após a terceira tentativa de login. Outras vezes, pode levar de 5 a 10 minutos antes que a mensagem de bloqueio seja exibida. Continue esse processo até receber a mensagem de bloqueio, quando a conta da Patti será temporariamente bloqueada para impedir o acesso não autorizado.

29. Você não conseguirá fazer login novamente como Patti até que a** duração do bloqueio de 90 segundos** definida anteriormente expire. <br/>

    Após sua conta ter sido bloqueada, aguarde 90 segundos e entre novamente como **pattif@xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo de locatário atribuído a você pelo provedor de hospedagem do seu laboratório). No campo **Senha**, digite a senha da Patti, que é a **Senha de usuário** fornecida pelo provedor de hospedagem do laboratório. Se necessário, conclua o processo de login do MFA. Verifique se você consegue fazer login com sucesso usando a conta da Patti.

30. Assim que seu login for bem-sucedido, você poderá fechar todos os aplicativos abertos. Esse será seu último exercício de laboratório usando o controlador de domínio LON-DC1.
 
# Prosseguir para o Laboratório 2, Exercício 2
