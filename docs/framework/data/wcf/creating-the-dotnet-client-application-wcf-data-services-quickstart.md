---
title: "Création de l'application cliente .NET Framework (démarrage rapide des services de données WCF)"
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
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d654ad24f8d23a47d2a3be3b07c42c104bb9b70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Création de l'application cliente .NET Framework (démarrage rapide des services de données WCF)
C’est la dernière tâche de la [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] démarrage rapide. Dans cette tâche, vous sera ajouter une application console à la solution, ajoutez une référence à la [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] dans cette nouvelle application cliente et l’accès de flux le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux à partir de l’application cliente en utilisant les classes de service de données client générées et le client bibliothèques.  
  
> [!NOTE]
>  Il n'est pas obligatoire pour une application cliente .NET Framework d'accéder à un flux de données. Le service de données est accessible pour tout composant d'application qui consomme un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Pour plus d’informations, consultez [à l’aide d’un Service de données dans une Application cliente](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>Pour créer l'application cliente à l'aide de Visual Studio  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit de la solution, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
2.  Dans **types de projet**, cliquez sur **Windows**, puis sélectionnez **Application WPF** dans les **modèles** volet.  
  
3.  Entrez `NorthwindClient` pour le nom du projet, puis cliquez sur **OK**.  
  
4.  Ouvrez le fichier MainWindow.xaml et remplacez le code XAML par le code suivant :  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>Pour ajouter une référence de service de données au projet  
  
1.  Cliquez sur le projet NorthwindClient, cliquez sur **ajouter une référence de Service**, puis cliquez sur **Discover**.  
  
     Cette opération affiche le service de données Northwind que vous avez créé dans la première tâche.  
  
2.  Dans le **Namespace** zone de texte, tapez `Northwind`, puis cliquez sur **OK**.  
  
     Cette opération ajoute un nouveau fichier de code au projet qui contient les classes de données utilisées pour accéder et interagir avec les ressources du service de données sous la forme d'objets. Les classes de données sont créées dans l'espace de noms `NorthwindClient.Northwind`.  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>Pour accéder aux données du service des données dans l'application WPF  
  
1.  Dans **l’Explorateur de solutions** sous **NorthwindClient**, cliquez sur le projet, cliquez sur **ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence, cliquez sur le **.NET** onglet, sélectionnez l’assembly System.Data.Services.Client.dll, puis cliquez sur **OK**. Dans **l’Explorateur de solutions** sous **NorthwindClient**, ouvrez la page de codes pour le fichier MainWindow.xaml et ajoutez le code suivant `using` instruction (`Imports` en Visual Basic).  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  Insérez le code suivant qui interroge le service de données et lie le résultat à une <xref:System.Data.Services.Client.DataServiceCollection%601> dans la classe `MainWindow`:  
  
    > [!NOTE]
    >  Vous devez remplacer le nom d'hôte `localhost:12345` par le serveur et le port qui hébergent votre instance du service de données Northwind.  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  Insérez le code suivant qui enregistre les modifications dans la classe `MainWindow` :  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a>Pour générer et exécuter l'application NothwindClient  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet NorthwindClient et sélectionnez **définir comme projet de démarrage**.  
  
2.  Appuyez sur F5 pour démarrer l'application.  
  
     Cette opération génère et démarre l'application cliente. Les données sont demandées auprès du service et s'affichent dans la console.  
  
3.  Modifier une valeur dans la **quantité** colonne de la grille de données, puis cliquez sur **enregistrer**.  
  
     Les modifications sont enregistrées sur le service de données.  
  
    > [!NOTE]
    >  Cette version de l'application NorthwindClient ne prend pas en charge l'ajout et la suppression d'entités.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé correctement l'application cliente qui accède à l'exemple de flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Northwind. Vous avez également terminé le démarrage rapide [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’accès à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux à partir d’un [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, consultez [bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Ressources](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
