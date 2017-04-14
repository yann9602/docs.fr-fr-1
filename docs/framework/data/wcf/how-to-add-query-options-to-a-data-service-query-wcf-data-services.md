---
title: "Proc&#233;dure&#160;: ajouter des options de requ&#234;te &#224; une requ&#234;te de service des donn&#233;es (WCF Data Services) | Microsoft Docs"
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
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ajouter des options de requ&#234;te &#224; une requ&#234;te de service des donn&#233;es (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet d'interroger un service de données depuis une application cliente .NET Framework à l'aide des classes de service de données client générées. Le plus simple est de créer une expression de requête LINQ \(langage\-integrated Query\) qui inclut les options de requête voulues.  Vous pouvez également appeler une série de méthodes de requête LINQ pour composer une requête équivalente.  Enfin, vous pouvez utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour ajouter des options de requête à une requête.  Dans tous ces cas, l'URI généré par le client inclut le jeu d'entités demandé et les options de requête sélectionnées appliquées.  Pour plus d'informations, consultez [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant montre comment composer une expression de requête LINQ qui retourne uniquement les commandes dont le coût de fret est supérieur à $30 et qui classe les résultats selon la date d'expédition dans l'ordre décroissant.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinq)]  
  
## Exemple  
 L'exemple suivant montre comment composer une requête LINQ à l'aide d'une des méthodes de requête LINQ équivalente à la requête précédente.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## Exemple  
 L'exemple suivant indique comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour créer un <xref:System.Data.Services.Client.DataServiceQuery%601> équivalent aux exemples précédents.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptions)]  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'option de requête `$orderby` pour filtrer et classer les objets Orders retournés par la propriété Freight.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
## Voir aussi  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [Procédure : projeter des résultats de requête](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)