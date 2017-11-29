---
title: "Création du service de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 37d32d938f49d0767594e0f141d5a463ad5fc95f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-data-service"></a>Création du service de données
Dans cette tâche, vous allez créer un exemple de service de données qui utilise [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour exposer un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux basé sur la base de données Northwind. La tâche implique les étapes fondamentales suivantes :  
  
1.  Créez une application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
2.  Définissez le modèle de données à l'aide des outils [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
3.  Ajoutez le service de données à l'application Web.  
  
4.  Activez l'accès au service de données.  
  
> [!NOTE]
>  L'application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que vous créez lorsque vous effectuez cette tâche s'exécute sur le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fourni par [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] prend uniquement en charge l'accès à partir de l'ordinateur local. Pour simplifier les opérations de test et de dépannage du service de données pendant le développement, envisagez d'exécuter l'application qui héberge le service de données à l'aide des Services IIS (Internet Information Services). Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### <a name="to-create-the-aspnet-web-application"></a>Pour créer l'application Web ASP.NET  
  
1.  Dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], dans le **fichier** menu, sélectionnez **nouveau**, puis sélectionnez **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sous [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] sélectionner le **Web** modèle, puis sélectionnez **Application Web ASP.NET**.  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, vous devrez créer un nouveau site Web au lieu d'une nouvelle application Web.  
  
3.  Type `NorthwindService` en tant que le nom du projet.  
  
4.  Cliquez sur **OK**.  
  
5.  (Facultatif) Spécifiez un numéro de port spécifique pour votre application Web. Remarque : le numéro de port `12345` est utilisé pour le reste du démarrage rapide.  
  
    1.  Dans **l’Explorateur de solutions**, cliquez sur le nom de la [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet que vous venez créé, puis cliquez sur **propriétés**.  
  
    2.  Sélectionnez le **Web** onglet et définir la valeur de la **port spécifique** zone de texte `12345`.  
  
### <a name="to-define-the-data-model"></a>Pour définir le modèle de données  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nom de la [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet, puis cliquez sur **ajouter un nouvel élément.**  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur le **données** modèle, puis sélectionnez **ADO.NET Entity Data Model**.  
  
3.  Tapez le nom du modèle de données `Northwind.edmx`.  
  
4.  Dans le [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Assistant, sélectionnez **générer à partir de la base de données**, puis cliquez sur **suivant**.  
  
5.  Connecter le modèle de données à la base de données en effectuant l’une des étapes suivantes, puis cliquez sur **suivant**:  
  
    -   Si vous n’avez pas d’une connexion de base de données déjà configurée, cliquez sur **nouvelle connexion** et créer une nouvelle connexion. Pour plus d’informations, consultez [Comment : créer des connexions aux bases de données SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). Cette instance [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] doit avoir l'exemple de base de données Northwind joint.  
  
         \- ou -  
  
    -   Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.  
  
6.  Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.  
  
7.  Cliquez sur **Terminer** pour fermer l’Assistant.  
  
    > [!NOTE]
    >  Ce modèle de données généré expose les propriétés de clé étrangère sur les types d'entité. Les modèles de données créés à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 n'incluent pas ces propriétés de clé étrangère. Vous devez donc mettre à jour les classes de service de données clientes de toutes les applications clientes créées pour accéder au service de données Northwind créé à l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 avant d'essayer d'accéder à cette version du service de données Northwind.  
  
### <a name="to-create-the-data-service"></a>Pour créer le service de données  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nom de votre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet, puis cliquez sur **ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données WCF**.  
  
3.  Tapez le nom du service `Northwind`.  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut. Dans **l’Explorateur de solutions**, le service aura le nom, Northwind, avec l’extension. svc.cs ou. svc.vb.  
  
4.  Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`. La définition de classe doit ressembler aux éléments suivants:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>Pour activer l'accès aux ressources du service de données  
  
1.  Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Cela permet aux clients autorisés d'accéder aux ressources en lecture et en écriture pour les jeux d'entités spécifiés.  
  
    > [!NOTE]
    >  Tout client qui peut accéder à l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peut également accéder aux ressources exposées par le service de données. Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même. Pour plus d'informations, consultez [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé un nouveau service de données qui expose un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux basé sur la base de données Northwind et que vous avez activé l’accès au flux pour les clients qui ont des autorisations sur le [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application Web. Vous démarrerez ensuite le service de données à partir de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] et vous allez accéder à la [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux en soumettant des demandes HTTP GET via un navigateur Web :  
  
 [L’accès au Service à partir d’un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Outils ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
