---
title: "Cr&#233;ation de l&#39;application cliente .NET Framework (d&#233;marrage rapide WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Cr&#233;ation de l&#39;application cliente .NET Framework (d&#233;marrage rapide WCF Data Services)
Il s'agit de la dernière tâche du démarrage rapide [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  Dans cette tâche, vous allez ajouter une application console à la solution, une référence au flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] dans cette nouvelle application cliente et accéder au flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de l'application cliente à l'aide des classes de service de données client et des bibliothèques clientes générées.  
  
> [!NOTE]
>  Il n'est pas obligatoire pour une application cliente .NET Framework d'accéder à un flux de données.  Le service de données est accessible pour tout composant d'application qui consomme un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  Pour plus d'informations, consultez [Utilisation d'un service de données dans une application cliente](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
### Pour créer l'application cliente à l'aide de Visual Studio  
  
1.  Cliquez avec le bouton droit sur la solution dans l'**Explorateur de solutions**, cliquez sur **Ajouter**, puis sur **Nouveau projet**.  
  
2.  Dans **Types de projet**, cliquez sur **Windows**, puis sélectionnez **Application WPF** dans le volet **Modèles**.  
  
3.  Entrez `NorthwindClient` comme nom de projet, puis cliquez sur **OK**.  
  
4.  Ouvrez le fichier MainWindow.xaml et remplacez le code XAML par le code suivant :  
  
     [!code-xml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### Pour ajouter une référence de service de données au projet  
  
1.  Cliquez avec le bouton droit sur le projet NorthwindClient, puis cliquez sur **Ajouter une référence de service**, puis sur **Découvrir**.  
  
     Cette opération affiche le service de données Northwind que vous avez créé dans la première tâche.  
  
2.  Dans la zone de texte **Espace de noms**, tapez `Northwind`, puis cliquez sur **OK**.  
  
     Cette opération ajoute un nouveau fichier de code au projet qui contient les classes de données utilisées pour accéder et interagir avec les ressources du service de données sous la forme d'objets.  Les classes de données sont créées dans l'espace de noms `NorthwindClient.Northwind`.  
  
### Pour accéder aux données du service des données dans l'application WPF  
  
1.  Dans l'**Explorateur de solutions** sous **NorthwindClient**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence, cliquez sur l'onglet **.NET**, sélectionnez l'assembly System.Data.Services.Client.dll, puis cliquez sur **OK**.  Dans l'**Explorateur de solutions** sous **NorthwindClient**, ouvrez la page de codes pour le fichier MainWindow.xaml et ajoutez l'instruction  `using` suivante \(`Imports` en Visual Basic\).  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  Insérez le code suivant qui interroge le service de données et lie le résultat à une <xref:System.Data.Services.Client.DataServiceCollection%601> dans la classe `MainWindow`:  
  
    > [!NOTE]
    >  Vous devez remplacer le nom d'hôte `localhost:12345` par le serveur et le port qui hébergent votre instance du service de données Northwind.  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  Insérez le code suivant qui enregistre les modifications dans la classe `MainWindow` :  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### Pour générer et exécuter l'application NothwindClient  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet NorthwindClient et sélectionnez **Définir comme projet de démarrage**.  
  
2.  Appuyez sur F5 pour démarrer l'application.  
  
     Cette opération génère et démarre l'application cliente.  Les données sont demandées auprès du service et s'affichent dans la console.  
  
3.  Modifiez une valeur dans la colonne **Quantité** de la grille de données, puis cliquez sur **Enregistrer**.  
  
     Les modifications sont enregistrées sur le service de données.  
  
    > [!NOTE]
    >  Cette version de l'application NorthwindClient ne prend pas en charge l'ajout et la suppression d'entités.  
  
## Étapes suivantes  
 Vous avez créé correctement l'application cliente qui accède à l'exemple de flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Northwind.  Vous avez également terminé le démarrage rapide [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'accès à un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à partir d'une application [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consultez [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
## Voir aussi  
 [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [Ressources](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)