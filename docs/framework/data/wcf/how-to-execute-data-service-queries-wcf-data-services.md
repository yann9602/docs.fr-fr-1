---
title: "Proc&#233;dure&#160;: ex&#233;cuter des requ&#234;tes de service des donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "interrogation du service de données [WCF Data Services]"
  - "Services de données WCF, accès aux données"
  - "Services de données WCF, interroger"
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ex&#233;cuter des requ&#234;tes de service des donn&#233;es (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet d'interroger un service de données depuis une application cliente .NET Framework à l'aide des classes de service de données client générées.  Vous pouvez exécuter des requêtes à l'aide d'une des méthodes suivantes :  
  
-   Exécution d'une requête LINQ sur la <xref:System.Data.Services.Client.DataServiceQuery%601> nommée que vous obtenez du <xref:System.Data.Services.Client.DataServiceContext> que l'outil `Add Data Service Reference` génère.  
  
-   Implicitement, en énumérant sur la <xref:System.Data.Services.Client.DataServiceQuery%601> nommée que vous obtenez du <xref:System.Data.Services.Client.DataServiceContext> que l'outil `Add Data Service Reference` génère.  
  
-   Explicitement, en appelant la méthode <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> sur <xref:System.Data.Services.Client.DataServiceQuery%601>, ou la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> pour une exécution asynchrone.  
  
 Pour plus d'informations, consultez [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant montre comment définir et exécuter une requête LINQ qui retourne tous les `Customers` sur le service de données Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## Exemple  
 L'exemple suivant montre comment utiliser le contexte que l'outil `Add Data Service Reference` génère pour exécuter implicitement une requête qui retourne tous les `Customers` sur le service de données Northwind.  L'URI du jeu d'entités `Customers` demandé est déterminé automatiquement par le contexte.  La requête est exécutée implicitement lorsque l'énumération se produit.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## Exemple  
 L'exemple suivant montre comment utiliser <xref:System.Data.Services.Client.DataServiceContext> pour exécuter explicitement une requête qui retourne tous les `Customers` sur le service de données Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## Voir aussi  
 [Procédure : ajouter des options de requête à une requête de service des données](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)