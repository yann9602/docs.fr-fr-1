---
title: "Proc&#233;dure&#160;: d&#233;velopper un WCF Data Service qui fonctionne sur IIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, déploiement"
  - "Services de données WCF, développement"
  - "Services de données WCF, hébergement"
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: d&#233;velopper un WCF Data Service qui fonctionne sur IIS
Cette rubrique indique comment utiliser [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour créer un service de données d'après l'exemple de base de données Northwind hébergé par une application Web ASP.NET qui fonctionne sur les services IIS \(internet Information Services\).  Pour obtenir un exemple montrant comment créer le même service de données Northwind qu'une application Web ASP.NET qui s'exécute sur le serveur de développement ASP.NET, consultez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
> [!NOTE]
>  Pour créer le service de données Northwind, vous avez dû installer l'exemple de base de données Northwind sur l'ordinateur local.  Pour télécharger cet exemple de base de données, consultez la page de téléchargement, [Exemples de bases de données pour SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).  
  
 Cette rubrique indique comment créer un service de données à l'aide du fournisseur Entity Framework.  Il existe d'autres fournisseurs de services de données.  Pour plus d'informations, consultez [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
 Après avoir créé le service, vous devez explicitement fournir un accès aux ressources du service de données.  Pour plus d'informations, consultez [Procédure : activer l'accès au service de données](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
### Pour créer l'application Web ASP.NET qui s'exécute sur les services IIS  
  
1.  Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau**, puis **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez Visual Basic ou Visual C\# comme langage de programmation.  
  
3.  Dans le volet **Modèles**, sélectionnez **Application Web ASP.NET**.  Remarque : si vous utilisez Visual Studio Web Developer, vous devrez créer un nouveau site Web au lieu d'une nouvelle application Web.  
  
4.  Tapez `NorthwindService` comme nom du projet.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans le menu **Projet**, sélectionnez **Propriétés NorthwindService**.  
  
7.  Sélectionnez l'onglet **Web**, puis sélectionnez **Utiliser le serveur Web IIS local**.  
  
8.  Cliquez sur **Créer un répertoire virtuel**, puis sur **OK**.  
  
9. À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes \(en fonction du système d'exploitation\) :  
  
    -   Systèmes 32 bits :  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   Systèmes 64 bits :  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     Cela permet de vérifier que Windows Communication Foundation \(WCF\) est inscrit sur l'ordinateur.  
  
10. À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes \(en fonction du système d'exploitation\) :  
  
    -   Systèmes 32 bits :  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   Systèmes 64 bits :  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     Cela permet de s'assurer qu'IIS s'exécute correctement après que WCF a été installé sur l'ordinateur.  Vous devrez peut\-être redémarrer IIS.  
  
11. Lorsque l'application ASP.NET s'exécute sur IIS7, vous devez aussi effectuer les étapes suivantes :  
  
    1.  Ouvrez le Gestionnaire des services Internet et accédez à l'application PhotoService sous **Site Web par défaut**.  
  
    2.  Dans **Affichage des fonctionnalités**, double\-cliquez sur **Authentification**.  
  
    3.  Sur la page **Authentification**, sélectionnez **Authentification anonyme**.  
  
    4.  Dans le volet **Actions**, cliquez sur **Modifier** pour définir le principal de sécurité sous lequel les utilisateurs anonymes se connecteront au site.  
  
    5.  Dans la boîte de dialogue **Modifier les informations d'identification anonyme**, sélectionnez **Identité du pool d'applications**.  
  
    > [!IMPORTANT]
    >  Lorsque vous utilisez le compte de service réseau, vous accordez aux utilisateurs anonymes l'accès à tout le réseau interne associé à ce compte.  
  
12. En utilisant SQL Server Management Studio, l'utilitaire sqlcmd.exe ou l'Éditeur Transact\-SQL dans Visual Studio, exécutez la commande Transact\-SQL suivante sur l'instance SQL Server à laquelle la base de données Northwind est attachée :  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     Cela crée une connexion dans l'instance SQL Server pour le compte Windows utilisé pour exécuter IIS.  Cela permet à IIS de se connecter à l'instance de SQL Server.  
  
13. Avec la base de données Northwind attachée, exécutez les commandes Transact\-SQL suivantes :  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     Cela accorde des droits à la nouvelle connexion et permet à IIS de lire et d'écrire les données dans la base de données Northwind.  
  
### Pour définir le modèle de données  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet ASP.NET, puis cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **ADO.NET Entity Data Model**.  
  
3.  Tapez `Northwind.edmx` pour le nom du modèle de données.  
  
4.  Dans l'Assistant EDM, sélectionnez **Générer à partir de la base de données**, puis cliquez sur **Suivant**.  
  
5.  Connectez le modèle de données à la base de données en suivant l'une des étapes suivantes puis cliquez sur **Suivant** :  
  
    -   Si vous n'avez pas une connexion de base de données déjà configurée, cliquez sur **Nouvelle connexion** puis créez une nouvelle connexion.  Pour plus d'informations, consultez [Procédure : création de connexions à des bases de données SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).  Cette instance [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] doit avoir l'exemple de base de données Northwind joint.  
  
         ou  
  
    -   Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.  
  
6.  Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.  
  
7.  Cliquez sur **Terminer** pour fermer l'Assistant.  
  
    > [!NOTE]
    >  Ce modèle de données généré expose les propriétés de clé étrangère sur les types d'entité.  Les modèles de données créés à l'aide de Visual Studio 2008 n'incluent pas ces propriétés de clé étrangère.  Vous devez donc mettre à jour les classes de service de données clientes de toutes les applications clientes créées pour accéder au service de données Northwind créé à l'aide de Visual Studio 2008 avant d'essayer d'accéder à cette version du service de données Northwind.  
  
### Pour créer le service de données  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.NET, puis cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans cette boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **ADO.NET Data Service**.  
  
3.  Tapez `Northwind` pour le nom du service.  
  
     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.  La fenêtre de l'éditeur de code s'ouvre par défaut.  Dans l'**Explorateur de solutions**, le service aura le nom, Northwind, avec l'extension .svc.cs ou .svc.vb.  
  
4.  Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`.  La définition de classe doit ressembler aux éléments suivants:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## Voir aussi  
 [Exposition de vos données comme un service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)