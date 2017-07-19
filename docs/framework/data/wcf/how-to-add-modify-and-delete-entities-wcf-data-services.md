---
title: "Proc&#233;dure&#160;: ajouter, modifier et supprimer des entit&#233;s (WCF Data Services) | Microsoft Docs"
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
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ajouter, modifier et supprimer des entit&#233;s (WCF Data Services)
Avec les bibliothèques clientes [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez créer, mettre à jour et supprimer des données d'entité dans un service de données en effectuant des actions équivalentes sur les objets dans <xref:System.Data.Services.Client.DataServiceContext> Pour plus d'informations, consultez [Mise à jour du service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant crée une instance de l'objet puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer l'élément dans le contexte.  Un message HTTP POST est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## Exemple  
 L'exemple suivant récupère et modifie un objet existant puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour marquer l'élément dans le contexte comme mis à jour.  Un message HTTP MERGE est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## Exemple  
 L'exemple suivant appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour marquer l'élément dans le contexte comme supprimé.  Un message HTTP DELETE est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## Exemple  
 L'exemple suivant crée une nouvelle instance de l'objet puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer l'élément dans le contexte avec le lien vers l'ordre connexe.  Un message HTTP POST est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [Procédure : joindre une entité existante à DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)   
 [Procédure : définir des relations d'entité](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)   
 [Opérations de traitement par lot](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)