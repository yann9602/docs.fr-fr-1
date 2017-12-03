---
title: "Comment : ajouter, modifier et supprimer des entités (services de données WCF)"
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
helpviewer_keywords: WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e41502fee9cfa272b154f6ddaf0e6a41a482bc7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Comment : ajouter, modifier et supprimer des entités (services de données WCF)
Avec la [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] les bibliothèques clientes, vous pouvez créer, mettre à jour et supprimer des données d’entité dans un service de données en effectuant des actions équivalentes sur des objets dans le <xref:System.Data.Services.Client.DataServiceContext>. Pour plus d’informations, consultez [mise à jour du Service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée une instance de l'objet puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer l'élément dans le contexte. Un message HTTP POST est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant récupère et modifie un objet existant puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour marquer l'élément dans le contexte comme mis à jour. Un message HTTP MERGE est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour marquer l'élément dans le contexte comme supprimé. Un message HTTP DELETE est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée une nouvelle instance de l'objet puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer l'élément dans le contexte avec le lien vers l'ordre connexe. Un message HTTP POST est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Comment : attacher une entité existante au DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)  
 [Comment : définir des relations d’entités](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)  
 [Opérations de traitement par lot](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
