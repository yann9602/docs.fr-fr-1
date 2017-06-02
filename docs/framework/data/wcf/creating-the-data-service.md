---
title: "Cr&#233;ation du service de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Cr&#233;ation du service de donn&#233;es
Dans cette tâche, vous allez créer un exemple de service de données qui utilise [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour exposer un flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] basé sur l'exemple de base de données Northwind. La tâche comprend les étapes de base suivantes :  
  
1.  Créez une application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
2.  Définissez le modèle de données à l'aide des outils [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
3.  Ajoutez le service de données à l'application Web.  
  
4.  Activez l'accès au service de données.  
  
> [!NOTE]
>  L'application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que vous créez lorsque vous effectuez cette tâche s'exécute sur le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fourni par [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  Le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] prend uniquement en charge l'accès à partir de l'ordinateur local.  Pour simplifier les opérations de test et de dépannage du service de données pendant le développement, envisagez d'exécuter l'application qui héberge le service de données à l'aide des Services IIS \(Internet Information Services\).  Pour plus d'informations, consultez [Procédure : développer un WCF Data Service qui fonctionne sur IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### Pour créer l'application Web ASP.NET  
  
1.  Dans le menu **Fichier** de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], sélectionnez **Nouveau**, puis **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], sélectionnez le modèle **Web**, puis **Application Web ASP.NET**.  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, vous devrez créer un nouveau site Web au lieu d'une nouvelle application Web.  
  
3.  Tapez `NorthwindService` comme nom du projet.  
  
4.  Cliquez sur **OK**.  
  
5.  \(Facultatif\) Spécifiez un numéro de port spécifique pour votre application Web.  Remarque : le numéro de port `12345` est utilisé pour le reste du démarrage rapide.  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que vous venez de créer, puis cliquez sur **Propriétés**.  
  
    2.  Sélectionnez l'onglet **Web** et définissez la valeur de la zone de texte **Port spécifique** sur `12345`.  
  
### Pour définir le modèle de données  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], puis cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur le modèle **Données**, puis sélectionnez **ADO.NET Entity Data Model**.  
  
3.  Tapez `Northwind.edmx` pour le nom du modèle de données.  
  
4.  Dans l'Assistant [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], sélectionnez **Générer à partir de la base de données**, puis cliquez sur **Suivant**.  
  
5.  Connectez le modèle de données à la base de données en suivant l'une des étapes suivantes puis cliquez sur **Suivant** :  
  
    -   Si vous n'avez pas une connexion de base de données déjà configurée, cliquez sur **Nouvelle connexion** puis créez une nouvelle connexion.  Pour plus d'informations, consultez [Procédure : création de connexions à des bases de données SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).  Cette instance [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] doit avoir l'exemple de base de données Northwind joint.  
  
         ou  
  
    -   Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.  
  
6.  Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.  
  
7.  Cliquez sur **Terminer** pour fermer l'Assistant.  
  
    > [!NOTE]
    >  Ce modèle de données généré expose les propriétés de clé étrangère sur les types d'entité.  Les modèles de données créés à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 n'incluent pas ces propriétés de clé étrangère.  Vous devez donc mettre à jour les classes de service de données clientes de toutes les applications clientes créées pour accéder au service de données Northwind créé à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 avant d'essayer d'accéder à cette version du service de données Northwind.  
  
### Pour créer le service de données  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], puis cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Service de données WCF**.  
  
3.  Tapez `Northwind` pour le nom du service.  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.  La fenêtre de l'éditeur de code s'ouvre par défaut.  Dans l'**Explorateur de solutions**, le service aura le nom, Northwind, avec l'extension .svc.cs ou .svc.vb.  
  
4.  Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`.  La définition de classe doit ressembler aux éléments suivants:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### Pour activer l'accès aux ressources du service de données  
  
1.  Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Cela permet aux clients autorisés d'accéder aux ressources en lecture et en écriture pour les jeux d'entités spécifiés.  
  
    > [!NOTE]
    >  Tout client qui peut accéder à l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peut également accéder aux ressources exposées par le service de données.  Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle\-même.  Pour plus d'informations, consultez [Sécurisation de WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## Étapes suivantes  
 Vous avez pu créer un nouveau service de données qui expose un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] basé sur l'exemple de base de données Northwind, et vous avez activé l'accès au flux pour les clients qui ont des autorisations sur l'application Web  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  Vous démarrerez ensuite le service de données à partir de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] et vous accéderez au flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] en soumettant des demandes HTTP GET via un navigateur Web :  
  
 [Accès au service à partir d'un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## Voir aussi  
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/fr-fr/91076853-0881-421b-837a-f582f36be527)