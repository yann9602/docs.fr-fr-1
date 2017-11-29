---
title: "Comment : créer un service de données à l’aide d’une source de données Entity Framework ADO.NET (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d69a3cf60b60806085a9bb7ae292cc88ba99871e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Comment : créer un service de données à l’aide d’une source de données Entity Framework ADO.NET (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expose les données d'entité comme un service de données. Ces données d'entité sont fournies par [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] lorsque la source de données est une base de données relationnelle. Cette rubrique vous indique comment créer un modèle de données basé sur [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dans une application Web [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] qui repose sur une base de données existante et utilise ce modèle de données pour créer un service de données.  
  
 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] fournit également un outil en ligne de commande qui peut générer un modèle [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] en dehors d'un projet [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Pour plus d’informations, consultez [Comment : utiliser des EdmGen.exe pour générer des fichiers de modèle et de mappage](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Pour ajouter à une application Web existante un modèle Entity Framework qui repose sur une base de données existante  
  
1.  Sur le **projet** menu, cliquez sur **ajouter un nouvel élément**.  
  
2.  Dans le **modèles** volet, cliquez sur le **données** catégorie, puis sélectionnez **ADO.NET Entity Data Model**.  
  
3.  Tapez le nom du modèle, puis **ajouter**.  
  
     La première page de l'Assistant [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
4.  Dans le **choisir le contenu du modèle** boîte de dialogue, sélectionnez **générer à partir de la base de données**. Cliquez ensuite sur **Suivant**.  
  
5.  Cliquez sur le **nouvelle connexion** bouton.  
  
6.  Dans le **propriétés de connexion** boîte de dialogue, tapez le nom de votre serveur, sélectionnez la méthode d’authentification, tapez le nom de la base de données, puis cliquez sur **OK**.  
  
     Le **choisir votre connexion de données**boîte de dialogue est mis à jour avec vos paramètres de connexion de base de données.  
  
7.  Vérifiez que le **enregistrer les paramètres de connexion de l’entité dans App.Config en tant que :** case à cocher est activée. Cliquez ensuite sur **Suivant**.  
  
8.  Dans le **choisir vos objets de base de données** boîte de dialogue, sélectionnez all de base de données des objets que vous envisagez d’exposer dans le service de données.  
  
    > [!NOTE]
    >  Les objets inclus dans le modèle de données ne sont pas exposés automatiquement par le service de données. Ils doivent être exposés explicitement par le service lui-même. Pour plus d’informations, consultez [configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
9. Cliquez sur **Terminer** pour terminer l’Assistant.  
  
     Cela crée un modèle de données par défaut basé sur la base de données spécifique. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] permet de personnaliser le modèle de données. Pour plus d’informations, consultez l’article [Tâches MSBuild](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Pour créer le service de données à l'aide du nouveau modèle de données  
  
1.  Dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], ouvrez le fichier .edmx qui représente le modèle de données.  
  
2.  Dans le **Explorateur de modèles**, cliquez sur le modèle, cliquez sur **propriétés**, puis notez le nom du conteneur d’entités.  
  
3.  Dans **l’Explorateur de solutions**, cliquez sur le nom de votre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projet, puis cliquez sur **ajouter un nouvel élément**.  
  
4.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données WCF**.  
  
5.  Fournissez un nom pour le service, puis cliquez sur **OK**.  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut.  
  
6.  Dans le code pour le service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui hérite de la classe <xref:System.Data.Objects.ObjectContext> et qui correspond au conteneur d'entités du modèle de données, noté à l'étape 2.  
  
7.  Dans le code pour le service de données, permettez aux clients autorisés d'accéder aux jeux d'entités exposés par le service de données. Pour plus d’informations, consultez [création du Service de données](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
8.  Pour tester le service de données Northwind.svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [l’accès au Service à partir d’un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Comment : créer un Service de données à l’aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Comment : créer un Service de données à l’aide d’un LINQ vers la Source de données SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
