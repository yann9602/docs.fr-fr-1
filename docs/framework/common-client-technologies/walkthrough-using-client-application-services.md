---
title: "Procédure pas à pas : utilisation des services d'application cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 64a27269ee6f3711f0c51f2c97cd8876c3ea6103
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-using-client-application-services"></a>Procédure pas à pas : utilisation des services d'application cliente
Cette rubrique décrit comment créer une application Windows qui utilise des services d'application cliente pour authentifier les utilisateurs et récupérer des rôles d'utilisateur et des paramètres.  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer une application Windows Forms et utiliser le concepteur de projets [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour activer et configurer les services d'application cliente ;  
  
-   créer une application de service web ASP.NET simple pour héberger les services d'application et tester votre configuration client ;  
  
-   ajouter l'authentification par formulaire à votre application. Vous commencerez par utiliser un nom d'utilisateur et un mot de passe codés en dur pour tester le service. vous ajouterez ensuite un formulaire de connexion en le définissant comme fournisseur d'informations d'identification dans la configuration de l'application ;  
  
-   ajouter des fonctionnalités basées sur les rôles, avec activation et affichage d'un bouton uniquement pour les utilisateurs ayant le rôle de gestionnaire (« manager ») ;  
  
-   accéder aux paramètres web. Vous commencerez par charger les paramètres web pour un utilisateur authentifié (test) sur la page **Paramètres** du concepteur de projets. Vous utiliserez ensuite le concepteur Windows Forms pour lier une zone de texte à un paramètre web. Enfin, vous enregistrerez la valeur modifiée sur le serveur ;  
  
-   implémenter la déconnexion. Vous ajouterez une option de déconnexion au formulaire et appellerez une méthode de déconnexion ;  
  
-   activer le mode hors connexion. Vous fournirez une case à cocher afin que les utilisateurs puissent spécifier leur état de connexion. Vous utiliserez ensuite cette valeur pour spécifier si les fournisseurs de services d'application cliente utiliseront les données mises en cache localement au lieu d'accéder à leurs services web. Enfin, vous authentifierez une nouvelle fois l'utilisateur actuel lorsque l'application repassera en mode en ligne.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer du composant suivant :  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>Création de l'application cliente  
 La première chose à faire est de créer un projet Windows Forms. Cette procédure pas à pas utilise des projets Windows Forms car ils sont davantage connus, mais le processus est semblable pour les projets Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Pour créer une application cliente et activer les services d'application cliente  
  
1.  Dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sélectionnez l’option de menu **Fichier &#124; Nouveau &#124; Projet**.  
  
2.  Dans le volet **Types de projets** de la boîte de dialogue **Nouveau projet**, développez le nœud **Visual Basic** ou **Visual C#**, puis sélectionnez le type de projet **Windows**.  
  
3.  Assurez-vous que **.NET Framework 3.5** est sélectionné, puis sélectionnez le modèle **Application Windows Forms** .  
  
4.  Remplacez le **Nom** du projet par `ClientAppServicesDemo`, puis cliquez sur **OK**.  
  
     Un nouveau projet Windows Forms est ouvert dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
5.  Dans le menu **Projet** , sélectionnez **Propriétés ClientAppServicesDemo**.  
  
     Le concepteur de projet s'affiche.  
  
6.  Sous l'onglet **Services** , sélectionnez **Activer les services d'application cliente**.  
  
7.  Vérifiez que l’option **Utiliser l’authentification par formulaire** est sélectionnée, puis affectez à **Emplacement du service d’authentification**, **Emplacement des services de rôles**et **Emplacement des services de paramètres web** la valeur `http://localhost:55555/AppServices`.  
  
8.  Pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], sous l'onglet **Application** , affectez à **Mode d'authentification** la valeur **Défini au niveau de l'application**.  
  
 Le concepteur stocke les paramètres spécifiés dans le fichier app.config de l'application.  
  
 À ce stade, l'application est configurée pour accéder aux trois services du même hôte. Dans la section suivante, vous allez créer l'hôte comme une application de service web simple, ce qui vous permettra de tester votre configuration client.  
  
## <a name="creating-the-application-services-host"></a>Création de l'hôte de services d'application  
 Dans cette section, vous allez créer une application de service web simple qui accède aux données utilisateur à partir d'un fichier de base de données SQL Server Compact local. Vous allez ensuite renseigner la base de données à l’aide de l’ [ASP.NET Web Site Administration Tool](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Cette configuration simple vous permet de tester rapidement votre application cliente. Vous pouvez également configurer l'hôte de service web de façon à ce qu'il accède aux données utilisateur d'une base de données SQL Server complète ou via les classes <xref:System.Web.Security.MembershipProvider> et <xref:System.Web.Security.RoleProvider> personnalisées. Pour plus d'informations, consultez [Creating and Configuring the Application Services Database for SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 Dans la procédure suivante, vous créez et configurez le service web AppServices.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Pour créer et configurer l'hôte de services d'application  
  
1.  Dans l’**Explorateur de solutions**, sélectionnez la solution ClientAppServicesDemo, puis dans le menu **Fichier**, sélectionnez **Ajouter | Nouveau projet**.  
  
2.  Dans le volet **Types de projets** de la boîte de dialogue **Nouveau projet**, développez le nœud **Visual Basic** ou **Visual C#**, puis sélectionnez le type de projet **Web**.  
  
3.  Assurez-vous que **.NET Framework 3.5** est sélectionné, puis sélectionnez le modèle **Application de service web ASP.NET** .  
  
4.  Remplacez le **Nom** du projet par `AppServices` , puis cliquez sur **OK**.  
  
     Un nouveau projet d'application de service web ASP.NET est ajouté à la solution, et le fichier Service1.asmx.vb ou le fichier Service1.asmx.cs apparaît dans l'éditeur.  
  
    > [!NOTE]
    >  Le fichier Service1.asmx.vb ou le fichier Service1.asmx.cs n'est pas utilisé dans cet exemple. Pour que votre environnement de travail ne soit pas encombré, vous pouvez le fermer et le supprimer de l' **Explorateur de solutions**.  
  
5.  Dans l' **Explorateur de solutions**, sélectionnez le projet AppServices, puis dans le menu **Projet** , sélectionnez **Propriétés AppServices**.  
  
     Le concepteur de projet s'affiche.  
  
6.  Sous l'onglet **Web** , assurez-vous que l'option **Utiliser le serveur de développement Visual Studio** est sélectionnée.  
  
7.  Sélectionnez **Port spécifique**, indiquez la valeur `55555`, puis affectez à **Chemin d’accès virtuel** la valeur `/AppServices`.  
  
8.  Enregistrez tous les fichiers.  
  
9. Dans l' **Explorateur de solutions**, ouvrez Web.config et recherchez la balise d'ouverture `<system.web>` .  
  
10. Ajoutez le balisage suivant avant la balise `<system.web>` .  
  
     Les éléments `authenticationService`, `profileService`et `roleService` de ce balisage activent et configurent les services d'application. À des fins de test, la valeur « false » est affectée à l'attribut `requireSSL` de l'élément `authenticationService` . Les attributs `readAccessProperties` et `writeAccessProperties` de l'élément `profileService` indiquent que la propriété `WebSettingsTestText` est en lecture/écriture.  
  
    > [!NOTE]
    >  Dans le code de production, vous devez toujours accéder au service d'authentification via le protocole SSL (Secure Sockets Layer, en utilisant le protocole HTTPS). Pour plus d’informations sur la configuration de SSL, consultez [Configuration de SSL (Secure Sockets Layer) (Guide des opérations IIS 6.0)](http://go.microsoft.com/fwlink/?LinkId=91844).  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. Ajoutez le balisage suivant après la balise d'ouverture `<system.web>` afin qu'il soit dans l'élément `<system.web>` .  
  
     L'élément `profile` configure un paramètre web unique nommé `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 Dans la procédure suivante, vous utilisez l'outil Administration de site Web ASP.NET pour effectuer la configuration du service et renseigner le fichier de base de données local. Vous allez ajouter deux utilisateurs nommés `employee` et `manager` qui appartiennent à deux rôles portant le même nom. Les mots de passe de ces utilisateurs sont `employee!` et `manager!` , respectivement.  
  
#### <a name="to-configure-membership-and-roles"></a>Pour configurer l'appartenance et les rôles  
  
1.  Dans l' **Explorateur de solutions**, sélectionnez le projet AppServices, puis dans le menu **Projet** , sélectionnez **Configuration ASP.NET**.  
  
     L' **outil Administration de site Web ASP.NET** s'affiche.  
  
2.  Sous l'onglet **Sécurité** , cliquez sur **Utilisez l'Assistant Installation de sécurité pour configurer la sécurité étape par étape**.  
  
     L' **Assistant Installation de sécurité** apparaît et affiche l'étape **Bienvenue** .  
  
3.  Cliquez sur **Suivant**.  
  
     L'étape **Sélectionnez une méthode accès** s'affiche.  
  
4.  Sélectionnez **À partir d'Internet**. Cela configure le service pour utiliser l'authentification par formulaire au lieu de l'authentification Windows.  
  
5.  Cliquez sur **Suivant** à deux reprises.  
  
     L'étape **Définissez les rôles** s'affiche.  
  
6.  Sélectionnez **Active les rôles pour ce site Web**.  
  
7.  Cliquez sur **Suivant**. Le formulaire **Créer un nouveau rôle** s'affiche.  
  
8.  Dans la zone de texte **Nouveau nom de rôle** , tapez `manager` , puis cliquez sur **Ajouter le rôle**.  
  
     La table **Rôles existants** apparaît avec la valeur spécifiée.  
  
9. Dans la zone de texte **Nouveau nom de rôle** , remplacez `manager` par `employee` , puis cliquez sur **Ajouter le rôle**.  
  
     La nouvelle valeur apparaît dans la table **Rôles existants** .  
  
10. Cliquez sur **Suivant**.  
  
     L'étape **Ajoutez de nouveaux utilisateurs** s'affiche.  
  
11. Dans le formulaire **Créer un utilisateur** , spécifiez les valeurs suivantes.  
  
  	|||  
  	|-|-|  
  	|**Nom d'utilisateur**|`manager`|  
  	|**Mot de passe**|`manager!`|  
  	|**Confirmer le mot de passe**|`manager!`|  
  	|**Message électronique**|`manager@contoso.com`|  
  	|**Question de sécurité**|`manager`|  
  	|**Réponse de sécurité**|`manager`|  
  
12. Cliquez sur **Créer un utilisateur**.  
  
     Un message indiquant la réussite de l'opération s'affiche.  
  
    > [!NOTE]
    >  Les valeurs **Adresse de messagerie**, **Question de sécurité**et **Réponse de sécurité** sont requises par le formulaire, mais ne sont pas utilisées dans cet exemple.  
  
13. Cliquez sur **Continuer**.  
  
     Le formulaire **Créer un utilisateur** s'affiche de nouveau.  
  
14. Dans le formulaire **Créer un utilisateur** , spécifiez les valeurs suivantes.  
  
  	|||  
  	|-|-|  
  	|**Nom d'utilisateur**|`employee`|  
  	|**Mot de passe**|`employee!`|  
  	|**Confirmer le mot de passe**|`employee!`|  
  	|**Message électronique**|`employee@contoso.com`|  
  	|**Question de sécurité**|`Employee`|  
  	|**Réponse de sécurité**|`employee`|  
  
15. Cliquez sur **Créer un utilisateur**.  
  
     Un message indiquant la réussite de l'opération s'affiche.  
  
16. Cliquez sur **Terminer**.  
  
     L' **outil Administration de site Web** s'affiche de nouveau.  
  
17. Cliquez sur **Utilisateurs manager**.  
  
     La liste des utilisateurs s'affiche.  
  
18. Cliquez sur **Modifier les rôles** pour l'utilisateur **employee** , puis sélectionnez le rôle **employee** .  
  
19. Cliquez sur **Modifier les rôles** pour l'utilisateur **manager** , puis sélectionnez le rôle **manager** .  
  
20. Fermez la fenêtre de navigateur qui héberge l' **outil Administration de site Web**.  
  
21. Si un message vous demandant si vous souhaitez recharger le fichier Web.config modifié s'affiche, cliquez sur **Oui**.  
  
 Cela termine la configuration du service web. À ce stade, vous pouvez appuyer sur F5 pour exécuter l'application cliente. Le **Serveur de développement ASP.NET** démarre alors automatiquement en même temps que votre application cliente. Le serveur continue de s'exécuter lorsque vous quittez l'application, mais redémarre en même temps que vous redémarrez l'application. Cela lui permet de détecter les modifications apportées à Web.config.  
  
 Pour arrêter le serveur manuellement, cliquez avec le bouton droit sur l'icône Serveur de développement ASP.NET dans la zone de notification de la barre des tâches, puis cliquez sur **Arrêter**. Il est parfois utile de vérifier qu'un redémarrage normal se produit.  
  
## <a name="adding-forms-authentication"></a>Ajout de l'authentification par formulaire  
 Dans la procédure suivante, vous ajoutez du code au formulaire principal qui essaie de valider l'utilisateur, puis qui refuse l'accès lorsque l'utilisateur fournit des informations d'identification non valides. Vous utilisez un nom d'utilisateur et un mot de passe codés en dur pour tester le service.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>Pour valider l'utilisateur dans votre code d'application  
  
1.  Dans l’**Explorateur de solutions**, ajoutez au projet ClientAppServicesDemo une référence à l’assembly System.Web.  
  
2.  Sélectionnez le fichier Form1, puis sélectionnez **Afficher | Code** dans le menu principal de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
3.  Dans l'éditeur de code, ajoutez les instructions suivantes en haut du fichier Form1.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]  [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  Dans l' **Explorateur de solutions**, double-cliquez sur Form1 pour afficher le concepteur.  
  
5.  Dans le concepteur, double-cliquez sur la surface de formulaire pour générer un gestionnaire d'événements <xref:System.Windows.Forms.Form.Load?displayProperty=fullName> nommé `Form1_Load`.  
  
     L'éditeur de code apparaît avec le curseur dans la méthode `Form1_Load` .  
  
6.  Ajoutez le code suivant à la méthode `Form1_Load` .  
  
     Ce code refuse l'accès aux utilisateurs non authentifiés en fermant l'application. Vous pouvez également autoriser les utilisateurs non authentifiés à accéder au formulaire, mais leur refuser l'accès à des fonctionnalités spécifiques. Normalement, vous ne codez pas en dur le nom d'utilisateur et le mot de passe, mais cela est utile à des fins de test. Dans la section suivante, vous remplacerez ce code par du code plus fiable qui affiche une boîte de dialogue de connexion et inclut la gestion des exceptions.  
  
     Notez que la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> se trouve dans [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Cette méthode délègue son travail au fournisseur d'authentification configuré et retourne la valeur `true` si l'authentification aboutit. Votre application ne requiert pas de référence directe au fournisseur d'authentification du client.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]  [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Vous pouvez maintenant appuyer sur F5 pour exécuter l'application : étant donné que vous fournissez un nom d'utilisateur et un mot de passe corrects, le formulaire s'affiche.  
  
> [!NOTE]
>  Si vous ne pouvez pas exécuter l'application, essayez d'arrêter le serveur de développement ASP.NET. Lorsque le serveur redémarre, vérifiez que la valeur 55555 est définie pour le port.  
  
 Pour afficher à la place le message d'erreur, modifiez les paramètres <xref:System.Web.Security.Membership.ValidateUser%2A> . Par exemple, remplacez le deuxième paramètre `"manager!"` par un mot de passe incorrect tel que `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Ajout d'un formulaire de connexion en tant que fournisseur d'informations d'identification  
 Vous pouvez obtenir les informations d'identification de l'utilisateur dans votre code d'application et les passer à la méthode <xref:System.Web.Security.Membership.ValidateUser%2A> . Toutefois, il est souvent utile de séparer le code d'acquisition des informations d'identification de votre code d'application, si vous souhaitez le modifier ultérieurement.  
  
 Dans la procédure suivante, vous configurez votre application de sorte qu'elle utilise un fournisseur d'informations d'identification, puis vous modifiez votre appel de méthode <xref:System.Web.Security.Membership.ValidateUser%2A> pour passer <xref:System.String.Empty> pour les deux paramètres. Les chaînes vides envoient un signal à la méthode <xref:System.Web.Security.Membership.ValidateUser%2A> pour appeler la méthode <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> du fournisseur d'informations d'identification configuré.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Pour configurer votre application de sorte qu'elle utilise un fournisseur d'informations d'identification  
  
1.  Dans l' **Explorateur de solutions**, sélectionnez le projet ClientAppServicesDemo, puis dans le menu **Projet** , sélectionnez **Propriétés ClientAppServicesDemo**.  
  
     Le concepteur de projet s'affiche.  
  
2.  Sous l'onglet **Services** , affectez à **Facultatif : Fournisseur d'informations d'identification** la valeur suivante. Cette valeur indique le nom de type qualifié d'assembly.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  Dans le fichier de code Form1, remplacez le code dans la méthode `Form1_Load` par le code suivant.  
  
     Ce code affiche un message d'accueil, puis appelle la méthode `ValidateUsingCredentialsProvider` que vous ajouterez dans l'étape suivante. Si l'utilisateur n'est pas authentifié, la méthode `ValidateUsingCredentialsProvider` retourne `false` et la méthode `Form1_Load` est retournée. Cela empêche tout code supplémentaire de s'exécuter avant la fermeture de l'application. Le message d'accueil est utile pour préciser ce point lorsque l'application redémarre. Vous ajouterez du code pour redémarrer l'application lorsque vous implémenterez la déconnexion à une étape ultérieure de cette procédure pas à pas.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]  [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Ajoutez la méthode suivante après la méthode `Form1_Load` .  
  
     Cette méthode passe des chaînes vides à la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> , ce qui provoque l'affichage de la boîte de dialogue Connexion. Si le service d'authentification n'est pas disponible, la méthode <xref:System.Web.Security.Membership.ValidateUser%2A> lève une <xref:System.Net.WebException>. Dans ce cas, la méthode `ValidateUsingCredentialsProvider` affiche un message d'avertissement et demande si l'utilisateur souhaite refaire une tentative en mode hors connexion. Cette fonctionnalité requiert la fonction **Enregistrer le hachage de mot de passe localement pour activer la connexion hors connexion** décrite dans [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Cette fonctionnalité est activée par défaut pour les nouveaux projets.  
  
     Si l'utilisateur n'est pas validé, la méthode `ValidateUsingCredentialsProvider` affiche un message d'erreur et ferme l'application. Enfin, cette méthode retourne le résultat de la tentative d'authentification.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]  [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Création d'un formulaire de connexion  
 Un fournisseur d'informations d'identification est une classe qui implémente l'interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> . Cette interface a une méthode unique nommée <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> qui retourne un objet <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> . Les procédures suivantes décrivent comment créer une boîte de dialogue de connexion qui implémente <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> pour s'afficher et retourner les informations d'identification spécifiées par l'utilisateur.  
  
 Des procédures distinctes sont fournies pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et C#, car [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] fournit un modèle **Formulaire de connexion** . Cela permet d'économiser du temps et des efforts de codage.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Pour créer une boîte de dialogue de connexion comme fournisseur d'informations d'identification dans Visual Basic  
  
1.  Dans l' **Explorateur de solutions**, sélectionnez le projet ClientAppServicesDemo, puis dans le menu **Projet** , sélectionnez **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle **Formulaire de connexion** , remplacez la valeur **Nom** par `Login.vb`, puis cliquez sur **Ajouter**.  
  
     La boîte de dialogue de connexion apparaît dans le Concepteur Windows Forms.  
  
3.  Dans le concepteur, cliquez sur **OK** , puis dans la fenêtre **Propriétés** , affectez à `DialogResult` la valeur `OK`.  
  
4.  Dans le concepteur, ajoutez un contrôle `CheckBox` au formulaire sous la zone de texte **Mot de passe** .  
  
5.  Dans la fenêtre **Propriétés**, spécifiez la valeur **(Nom)** `rememberMeCheckBox` et la valeur **Texte** `&Remember me`.  
  
6.  Sélectionnez **Afficher | Code** dans le menu principal de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
7.  Dans l'éditeur de code, ajoutez le code suivant en haut du fichier.  
  
     [!code-vb[ClientApplicationServices #101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Modifiez la signature de classe pour que la classe implémente l'interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. Assurez-vous que le curseur se trouve après `IClientformsAuthenticationCredentialsProvider`, puis appuyez sur Entrée pour générer la méthode `GetCredentials` .  
  
10. Localisez l'implémentation <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>, puis remplacez-la par le code suivant.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 La procédure C# suivante fournit la liste de code complète pour une boîte de dialogue de connexion simple. La disposition de cette boîte de dialogue est un peu brute, mais la partie importante est l'implémentation <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> .  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>Pour créer une boîte de dialogue de connexion comme fournisseur d'informations d'identification en C#  
  
1.  Dans l' **Explorateur de solutions**, sélectionnez le projet ClientAppServicesDemo, puis dans le menu **Projet** , sélectionnez **Ajouter une classe**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez la valeur **Nom** par `Login.cs`, puis cliquez sur **Ajouter**.  
  
     Le fichier Login.cs s'ouvre dans l'éditeur de code.  
  
3.  Remplacez le code par défaut par le code suivant.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Vous pouvez maintenant exécuter l'application et voir la boîte de dialogue de connexion. Pour tester ce code, essayez différentes informations d'identification, à la fois valides et non valides, et vérifiez que le formulaire n'est accessible qu'avec des informations d'identification valides. Les noms d’utilisateur valides sont `employee` et `manager` avec les mots de passe `employee!` et `manager!` , respectivement.  
  
> [!NOTE]
>  À ce stade, ne sélectionnez pas **Mémoriser mes informations** , car sinon vous ne pourrez pas vous connecter sous une autre identité tant que vous n'aurez pas implémenté la déconnexion à une étape ultérieure de cette procédure pas à pas.  
  
## <a name="adding-role-based-functionality"></a>Ajout de fonctionnalités basées sur les rôles  
 Dans la procédure suivante, vous ajoutez un bouton au formulaire et l'affichez uniquement pour les utilisateurs ayant le rôle manager.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Pour modifier l'interface utilisateur selon le rôle de l'utilisateur  
  
1.  Dans l’**Explorateur de solutions**, sélectionnez Form1 dans le projet ClientAppServicesDemo, puis sélectionnez **Afficher | Concepteur** dans le menu principal de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
2.  Dans le concepteur, ajoutez un contrôle <xref:System.Windows.Forms.Button> au formulaire à partir de la **Boîte à outils**.  
  
3.  Dans la fenêtre **Propriétés** , définissez les propriétés suivantes pour le bouton.  
  
  	|Propriété|Valeur|  
  	|--------------|-----------|  
  	|**(Name)**|managerOnlyButton|  
  	|**Text**|&Manager task|  
  	|**Visible**|`False`|  
  
4.  Dans l'éditeur de code pour Form1, ajoutez le code suivant à la fin de la méthode `Form1_Load`  
  
     Ce code appelle la méthode `DisplayButtonForManagerRole` que vous ajouterez à l'étape suivante.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]  [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Ajoutez la méthode suivante à la fin de la classe Form1.  
  
     Cette méthode appelle la méthode <xref:System.Security.Principal.IPrincipal.IsInRole%2A> du <xref:System.Security.Principal.IPrincipal> retourné par la propriété `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> . Pour les applications configurées pour utiliser les services d'application cliente, cette propriété retourne un <xref:System.Web.ClientServices.ClientRolePrincipal>. Étant donné que cette classe implémente l'interface <xref:System.Security.Principal.IPrincipal> , vous n'avez pas besoin de la référencer explicitement.  
  
     Si l'utilisateur est dans le rôle « manager », la méthode `DisplayButtonForManagerRole` affecte à la propriété <xref:System.Windows.Forms.Control.Visible%2A> du `managerOnlyButton` la valeur `true`. Si une <xref:System.Net.WebException> est levée, cette méthode affiche également un message d'erreur indiquant que le service de rôles n'est pas disponible.  
  
    > [!NOTE]
    >  La méthode <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> retourne toujours la valeur `false` si la connexion de l'utilisateur a expiré. Cela ne se produit pas si votre application appelle une fois la méthode <xref:System.Security.Principal.IPrincipal.IsInRole%2A> peu après l'authentification, comme indiqué dans l'exemple de code de cette procédure pas à pas. Si votre application doit récupérer des rôles d'utilisateur à d'autres moments, vous souhaitez peut-être ajouter du code pour revalider les utilisateurs dont la connexion a expiré. Si des rôles sont attribués à tous les utilisateurs valides, vous pouvez déterminer si la connexion a expiré en appelant la méthode <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=fullName> . Si aucun rôle n'est retourné, la connexion a expiré. Pour obtenir un exemple de cette fonctionnalité, consultez la méthode <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> . Cette fonctionnalité n'est requise que si vous avez sélectionné l'option **Imposer aux utilisateurs de se reconnecter chaque fois que le cookie du serveur expire** dans la configuration de votre application. Pour plus d'informations, consultez [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]  [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Si l'authentification aboutit, le fournisseur d'authentification du client affecte à la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> une instance de la classe <xref:System.Web.ClientServices.ClientRolePrincipal>. Cette classe implémente la méthode <xref:System.Security.Principal.IPrincipal.IsInRole%2A> afin que le travail soit délégué au fournisseur de rôles configuré. Comme avant, votre code d'application ne requiert pas de référence directe au fournisseur de services.  
  
 Vous pouvez maintenant exécuter l'application et ouvrir une session en tant qu'employé pour constater que le bouton n'apparaît pas, puis ouvrir une session en tant que responsable (« manager ») pour voir le bouton.  
  
## <a name="accessing-web-settings"></a>Accès aux paramètres web  
 Dans la procédure suivante, vous ajoutez une zone de texte au formulaire et vous la liez à un paramètre web. Comme le code précédent qui utilise l'authentification et les rôles, votre code de paramètres n'accède pas directement au fournisseur de paramètres. À la place, il utilise la classe `Settings` fortement typée (accessible en tant que `Properties.Settings.Default` en C# et en tant que `My.Settings` en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) générée pour votre projet par [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Pour utiliser des paramètres web dans votre interface utilisateur  
  
1.  Assurez-vous que le **serveur de développement web ASP.NET** s'exécute encore en vérifiant la zone de notification de la barre des tâches. Si vous avez arrêté le serveur, redémarrez l'application (ce qui démarre automatiquement le serveur), puis fermez la boîte de dialogue de connexion.  
  
2.  Dans l' **Explorateur de solutions**, sélectionnez le projet ClientAppServicesDemo, puis dans le menu **Projet** , sélectionnez **Propriétés ClientAppServicesDemo**.  
  
     Le concepteur de projet s'affiche.  
  
3.  Sous l'onglet **Paramètres** , cliquez sur **Charger les paramètres web**.  
  
     La boîte de dialogue **Connexion** s'affiche.  
  
4.  Entrez les informations d'identification de l'employé ou du gestionnaire, puis cliquez sur **Se connecter**. Dans la mesure où le paramètre web que vous utiliserez est configuré pour être accessible par les utilisateurs authentifiés uniquement, le fait de cliquer sur **Ignorer la connexion** ne charge aucun paramètre.  
  
     Le paramètre `WebSettingsTestText` apparaît dans le concepteur avec la valeur par défaut `DefaultText`. En outre, une classe `Settings` contenant une propriété `WebSettingsTestText` est générée pour votre projet.  
  
5.  Dans l’**Explorateur de solutions**, sélectionnez Form1 dans le projet ClientAppServicesDemo, puis sélectionnez **Afficher | Concepteur** dans le menu principal de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
6.  Dans le concepteur, ajoutez un contrôle <xref:System.Windows.Forms.TextBox> au formulaire.  
  
7.  Dans la fenêtre **Propriétés** , définissez la valeur **(Name)** sur `webSettingsTestTextBox`.  
  
8.  Dans l'éditeur de code, ajoutez le code suivant à la fin de la méthode `Form1_Load`  
  
     Ce code appelle la méthode `BindWebSettingsTestTextBox` que vous ajouterez à l'étape suivante.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]  [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Ajoutez la méthode suivante à la fin de la classe Form1.  
  
     Cette méthode lie la propriété <xref:System.Windows.Forms.TextBox.Text%2A> de l'élément `webSettingsTestTextBox` à la propriété `WebSettingsTestText` de la classe `Settings` générée précédemment dans cette procédure. Si une <xref:System.Net.WebException> est levée, cette méthode affiche également un message d'erreur indiquant que le service de paramètres web n'est pas disponible.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]   [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  En général, vous utilisez la liaison de données pour activer la communication bidirectionnelle automatique entre un contrôle et un paramètre web. Toutefois, vous pouvez aussi accéder directement aux paramètres web comme indiqué dans l'exemple suivant :  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]   [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. Dans le concepteur, sélectionnez le formulaire, puis dans la fenêtre **Propriétés** , cliquez sur le bouton **Événements** .  
  
11. Sélectionnez l'événement <xref:System.Windows.Forms.Form.FormClosing> , puis appuyez sur Entrée pour générer un gestionnaire d'événements.  
  
12. Remplacez la méthode générée par le code suivant.  
  
     Le gestionnaire d'événements <xref:System.Windows.Forms.Form.FormClosing> appelle la méthode `SaveSettings` , qui est également utilisée par les fonctionnalités de déconnexion que vous ajouterez dans la section suivante. La méthode `SaveSettings` vérifie tout d'abord que l'utilisateur ne s'est pas déconnecté. Pour ce faire, elle contrôle la propriété <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> du <xref:System.Security.Principal.IIdentity> retourné par l'entité de sécurité actuelle. L'entité de sécurité actuelle est extraite via la propriété `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> . Si l'utilisateur a été authentifié pour les services d'application cliente, le type d'authentification sera « ClientForms ». La méthode `SaveSettings` ne peut pas uniquement vérifier la propriété <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=fullName> , car l'utilisateur peut avoir une identité Windows valide après la déconnexion.  
  
     Si l'utilisateur ne s'est pas déconnecté, la méthode `SaveSettings` appelle la méthode <xref:System.Configuration.ApplicationSettingsBase.Save%2A> de la classe `Settings` générée précédemment dans cette procédure. Cette méthode peut lever une <xref:System.Net.WebException> si le cookie d'authentification a expiré. Cela se produit uniquement si vous avez sélectionné l'option **Imposer aux utilisateurs de se reconnecter chaque fois que le cookie du serveur expire** dans la configuration de votre application. Pour plus d'informations, consultez [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). La méthode `SaveSettings` gère l'expiration des cookies en appelant <xref:System.Web.Security.Membership.ValidateUser%2A> pour afficher la boîte de dialogue de connexion. Si l'utilisateur parvient à se connecter, la méthode `SaveSettings` tente d'enregistrer de nouveau les paramètres en s'appelant elle-même.  
  
     Comme dans le code précédent, la méthode `SaveSettings` affiche un message d'erreur si le service distant n'est pas disponible. Si le fournisseur de paramètres ne peut pas accéder au service distant, les paramètres sont encore enregistrés dans le cache local et rechargés lorsque l'application redémarre.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]  [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Ajoutez la méthode suivante à la fin de la classe Form1.  
  
     Ce code gère l'événement <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=fullName> et affiche un avertissement si l'un des paramètres n'a pas pu être enregistré. L'événement <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> ne se produit pas si le service de paramètres n'est pas disponible ou si le cookie d'authentification a expiré. L'événement <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> se produit par exemple si l'utilisateur s'est déjà déconnecté. Vous pouvez tester ce gestionnaire d'événements en ajoutant directement du code de déconnexion à la méthode `SaveSettings` avant l'appel de la méthode <xref:System.Configuration.ApplicationSettingsBase.Save%2A> . Le code de déconnexion que vous pouvez utiliser est décrit dans la section suivante.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]  [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. Pour C#, ajoutez le code suivant à la fin de la méthode `Form1_Load` . Ce code associe la méthode que vous avez ajoutée dans la dernière étape à l'événement <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved>.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Pour tester l'application à ce stade, exécutez-la plusieurs fois en tant qu'employé et en tant que gestionnaire (« manager »), et tapez des valeurs différentes dans la zone de texte. Les valeurs sont conservées d'une session à l'autre pour chaque utilisateur.  
  
## <a name="implementing-logout"></a>Implémentation de la déconnexion  
 Lorsque l'utilisateur coche la case **Mémoriser mes informations** au moment de la connexion, l'application authentifie automatiquement l'utilisateur lors des exécutions suivantes. L'authentification automatique continue ensuite pendant que l'application est en mode hors connexion ou jusqu'à ce que le cookie d'authentification expire. Toutefois, il peut arriver que plusieurs utilisateurs aient besoin d'accéder à l'application ou qu'un seul utilisateur se connecte avec des informations d'identification différentes. Pour permettre ce scénario, vous devez implémenter la fonctionnalité de déconnexion, comme décrit dans la procédure suivante.  
  
#### <a name="to-implement-logout-functionality"></a>Pour implémenter la fonctionnalité de déconnexion  
  
1.  Dans le concepteur Form1, ajoutez un contrôle <xref:System.Windows.Forms.Button> au formulaire à partir de la **Boîte à outils**.  
  
2.  Dans la fenêtre **Propriétés**, définissez la valeur **(Nom)** sur `logoutButton` et la valeur **Texte** sur **&Se déconnecter**.  
  
3.  Double-cliquez sur `logoutButton` pour générer un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click>.  
  
     L'éditeur de code apparaît avec le curseur dans la méthode `logoutButton_Click` .  
  
4.  Remplacez la méthode `logoutButton_Click` générée par le code suivant.  
  
     Ce gestionnaire d'événements appelle d'abord la méthode `SaveSettings` que vous avez ajoutée dans la section précédente. Il appelle ensuite la méthode <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=fullName> . Si le service d'authentification n'est pas disponible, la méthode <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> lève une <xref:System.Net.WebException>. Dans ce cas, la méthode `logoutButton_Click` affiche un message d'avertissement et passe temporairement en mode hors connexion pour déconnecter l'utilisateur. Le mode hors connexion est décrit dans la section suivante.  
  
     La déconnexion supprime le cookie d'authentification local afin que la connexion soit requise lorsque l'application est redémarrée. Après la déconnexion, le gestionnaire d'événements redémarre l'application. Lorsque celle-ci redémarre, elle affiche le message d'accueil, puis la boîte de dialogue de connexion. Le message d'accueil indique que l'application a redémarré. Cela empêche toute confusion potentielle si l'utilisateur doit se connecter pour enregistrer des paramètres, puis se connecter de nouveau car l'application a redémarré.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]  [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 Pour tester la fonctionnalité de déconnexion, exécutez l'application et sélectionnez **Mémoriser mes informations** dans la boîte de dialogue Connexion. Ensuite, fermez et redémarrez l'application pour vérifier que vous n'avez plus à vous connecter. Enfin, redémarrez l'application en cliquant sur Se déconnecter.  
  
## <a name="enabling-offline-mode"></a>Activation du mode hors connexion  
 Dans la procédure suivante, vous ajoutez une case à cocher au formulaire pour permettre à l'utilisateur de passer en mode hors connexion. Votre application indique le mode hors connexion en affectant à la propriété `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=fullName> la valeur `true`. L'état hors connexion est stocké sur le disque dur local à l'emplacement indiqué par la propriété <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=fullName> . Cela signifie que l'état hors connexion est stocké par utilisateur, pour chaque application.  
  
 En mode hors connexion, toutes les requêtes de service d'application cliente récupèrent des données du cache local au lieu de tenter d'accéder aux services. Dans la configuration par défaut, les données locales incluent une forme chiffrée du mot de passe de l'utilisateur. Cela permet à l'utilisateur de se connecter pendant que l'application est en mode hors connexion. Pour plus d'informations, consultez [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Pour activer le mode hors connexion dans votre application  
  
1.  Dans l’**Explorateur de solutions**, sélectionnez Form1 dans le projet ClientAppServicesDemo, puis sélectionnez **Afficher | Concepteur** dans le menu principal de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
2.  Dans le concepteur, ajoutez un contrôle <xref:System.Windows.Forms.CheckBox> au formulaire.  
  
3.  Dans la fenêtre **Propriétés**, définissez la valeur **(Nom)** sur `workOfflineCheckBox` et la valeur **Texte** sur **&Travailler hors connexion**.  
  
4.  Dans la fenêtre **Propriétés** , cliquez sur le bouton **Événements** .  
  
5.  Sélectionnez l'événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> , puis appuyez sur Entrée pour générer un gestionnaire d'événements.  
  
6.  Remplacez la méthode générée par le code suivant.  
  
     Ce code met à jour la valeur <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> et revalide silencieusement l'utilisateur lors du passage en mode en ligne. La méthode <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=fullName> utilise les informations d'identification mises en cache pour que l'utilisateur n'ait pas explicitement à se connecter. Si le service d'authentification n'est pas disponible, un message d'avertissement s'affiche et l'application reste hors connexion.  
  
    > [!NOTE]
    >  La méthode <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> est fournie pour des raisons pratiques uniquement. Étant donné qu'elle n'a pas de valeur de retour, elle ne peut pas indiquer si la revalidation a échoué. La revalidation peut, par exemple, échouer si les informations d'identification de l'utilisateur ont été modifiées sur le serveur. Dans ce cas, vous souhaitez peut-être inclure du code qui valide explicitement les utilisateurs après l'échec d'un appel de service. Pour plus d'informations, consultez la section Accès aux paramètres web, précédemment dans cette procédure pas à pas.  
  
     Après la revalidation, ce code enregistre toutes les modifications apportées aux paramètres web locaux en appelant la méthode `SaveSettings` que vous avez ajoutée précédemment. Il extrait ensuite toutes les nouvelles valeurs sur le serveur en appelant la méthode <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> de la classe `Settings` du projet (accessible en tant que `Properties.Settings.Default` en C# et en tant que `My.Settings` en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]  [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Ajoutez le code suivant à la fin de la méthode `Form1_Load` pour garantir que la case à cocher affiche l'état de connexion en cours.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]  [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Cela termine l'exemple d'application. Pour tester la fonction hors connexion, exécutez l'application, connectez-vous en tant qu'employé (« employee ») ou en tant que gestionnaire (« manager »), puis sélectionnez **Travailler hors connexion**. Modifiez la valeur de la zone de texte, puis fermez l'application. Redémarrez-la. Avant de vous connecter, cliquez avec le bouton droit sur l'icône Serveur de développement ASP.NET dans la zone de notification de la barre des tâches, puis cliquez sur **Arrêt**. Ensuite, connectez-vous normalement. Même si le serveur n'est pas en cours d'exécution, vous pouvez toujours vous connecter. Modifiez la valeur de la zone de texte, quittez l'application, puis redémarrez-la pour vérifier le changement de valeur.  
  
## <a name="summary"></a>Résumé  
 Dans cette procédure pas à pas, vous avez appris à activer et à utiliser les services d'application cliente dans une application Windows Forms. Après avoir configuré un serveur de test, vous avez ajouté du code à votre application pour authentifier les utilisateurs et récupérer du serveur des rôles d'utilisateur et des paramètres d'application. Vous avez également appris à activer le mode hors connexion pour que votre application utilise un cache de données local au lieu des services distants lorsque la connectivité n'est pas disponible.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans une application réelle, vous accédez aux données de nombreux utilisateurs à partir d'un serveur distant qui n'est pas toujours disponible ou peut tomber en panne sans prévenir. Pour garantir la fiabilité de votre application, vous devez gérer de manière appropriée les situations dans lesquelles le service n'est pas disponible. Cette procédure pas à pas inclut des blocs try/catch pour intercepter une <xref:System.Net.WebException> et afficher un message d'erreur lorsque le service n'est pas disponible. Dans le code de production, vous voudrez peut-être gérer ce cas en basculant en mode hors connexion, en quittant l'application ou en refusant l'accès à des fonctionnalités spécifiques.  
  
 Pour augmenter la sécurité de votre application, veillez à tester entièrement l'application et le serveur avant tout déploiement.  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’application cliente](../../../docs/framework/common-client-technologies/client-application-services.md)   
 [Vue d’ensemble des services d’application cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)   
 [Comment : configurer les services d’application cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)   
 [Outil Administration de site web ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)   
 [Création et configuration de la base de données des services d’application pour SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)   
 [Procédure pas à pas : utilisation des services d’application ASP.NET](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)

