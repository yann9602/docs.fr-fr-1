---
title: "Proc&#233;dure&#160;: joindre une entit&#233; existante &#224; DataServiceContext (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, changer des données"
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: joindre une entit&#233; existante &#224; DataServiceContext (WCF Data Services)
Lorsqu'une entité existe déjà dans un service de données, la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de joindre un objet qui représente directement l'entité au <xref:System.Data.Services.Client.DataServiceContext> sans exécuter d'abord une requête.  Pour plus d'informations, consultez [Mise à jour du service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant montre comment créer un objet `Customer` existant qui contient des modifications à enregistrer dans le service de données.  L'objet est joint au contexte et la méthode <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> est appelée pour marquer l'objet joint comme <xref:System.Data.Services.Client.EntityStates> avant d'appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)