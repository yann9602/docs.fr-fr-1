---
title: "Proc&#233;dure&#160;: ex&#233;cuter des requ&#234;tes asynchrones de service des donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "opérations asynchrones [WCF Data Services]"
  - "Services de données WCF, opérations asynchrones"
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ex&#233;cuter des requ&#234;tes asynchrones de service des donn&#233;es (WCF Data Services)
En utilisant la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez effectuer de façon asynchrone des opérations client\-serveur, telles que l'exécution de requêtes et l'enregistrement de modifications. Pour plus d'informations, consultez [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  Dans une application où le rappel doit être appelé sur un thread spécifique, vous devez marshaler explicitement l'exécution de la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>.  Pour plus d'informations, consultez [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant montre comment exécuter une requête asynchrone en appelant la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> pour démarrer la requête.  Le délégué inline delegate appelle la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pour afficher les résultats de la requête.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#executequeryasync)]  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)