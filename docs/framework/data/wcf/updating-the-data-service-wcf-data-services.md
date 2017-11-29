---
title: "Mise à jour du service de données (services de données WCF)"
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
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c86e755d35a57090941551de43aedd07c8f1f0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="updating-the-data-service-wcf-data-services"></a>Mise à jour du service de données (services de données WCF)
Lorsque vous utilisez la [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliothèque cliente pour consommer un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux, la bibliothèque traduit les entrées dans le flux en instances des classes de service de données client. Ces classes de service de données sont suivies à l'aide de l'objet <xref:System.Data.Services.Client.DataServiceContext> auquel <xref:System.Data.Services.Client.DataServiceQuery%601> appartient. Le client suit les modifications apportées aux entités que vous signalez à l'aide des méthodes sur <xref:System.Data.Services.Client.DataServiceContext>. Ces méthodes permettent au client de suivre les entités ajoutées et supprimées, ainsi que les modifications que vous apportez aux valeurs de propriété ou aux relations entre les instances d'entités. Ces modifications suivies sont renvoyées au service de données sous forme d'opérations REST lorsque vous appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
> [!NOTE]
>  Lorsque vous utilisez une instance de <xref:System.Data.Services.Client.DataServiceCollection%601> pour lier des données et des contrôles, les modifications apportées aux données dans le contrôle lié sont automatiquement signalées à l'objet <xref:System.Data.Services.Client.DataServiceContext>. Pour plus d’informations, consultez [liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Ajout, modification et changement d'entités  
 Lorsque vous utilisez la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux, les client données service classes résultantes chaque avoir statique *créer* méthode qui prend un paramètre pour chaque propriété d’entité non nullable. Vous pouvez utiliser cette méthode pour créer des instances de classes de type d'entité, comme dans l'exemple suivant :  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#createnewproduct)]  
  
 Pour ajouter une instance d’entité, appelez la *AddTo* méthode sur le <xref:System.Data.Services.Client.DataServiceContext> classe générée par le **ajouter une référence de Service** boîte de dialogue, comme dans l’exemple suivant :  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproductspecific)]  
  
 Cela ajoute l'objet au contexte et au jeu correct d'entités. Vous pouvez également appeler <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, mais vous devez fournir à la place le nom de jeu d'entités. Si l'entité ajoutée possède une ou plusieurs relations à d'autres entités, vous pouvez utiliser la méthode <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> ou l'une des méthodes précédentes et définir aussi explicitement ces liens. Ces opérations sont traitées plus loin dans cette rubrique.  
  
 Pour modifier une instance d'entité existante, recherchez tout d'abord cette entité, apportez les modifications souhaitées à ses propriétés, puis appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour indiquer à la bibliothèque cliente qu'elle doit envoyer une mise à jour de cet objet, comme illustré dans cet exemple :  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomerspecific)]  
  
 Pour supprimer une instance d'entité, appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext>, comme illustré dans l'exemple suivant :  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproductspecific)]  
  
 Pour plus d’informations, consultez [Comment : ajouter, modifier et supprimer des entités](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Attachement d'entités  
 La bibliothèque cliente vous permet d'enregistrer des mises à jour apportées à une entité sans exécuter en premier une requête pour charger l'entité dans <xref:System.Data.Services.Client.DataServiceContext>. Utilisez la méthode <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> pour joindre un objet existant à un jeu d'entités spécifique dans <xref:System.Data.Services.Client.DataServiceContext>. Vous pouvez modifier ensuite l'objet et enregistrer les modifications apportées au service de données. Dans l'exemple suivant, un objet client été modifié et joint au contexte, puis <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> est appelé pour marquer l'objet attaché comme <xref:System.Data.Services.Client.EntityStates.Modified> avant l'appel de <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> :  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobjectspecific)]  
  
 Vous devez tenir compte des points suivants lors de l'attachement d'objets :  
  
-   Un objet est joint dans l'état <xref:System.Data.Services.Client.EntityStates.Unchanged>.  
  
-   Lorsqu'un objet est joint, les objets associés à l'objet joint ne sont pas non plus joints.  
  
-   Un objet ne peut pas être joint si l'entité fait déjà l'objet d'un suivi par le contexte.  
  
-   La surcharge de méthode <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> qui utilise un paramètre `etag` est utilisée lorsque vous attachez un objet entité ayant été reçu avec une valeur eTag. Cette valeur eTag est ensuite utilisée pour vérifier l'accès concurrentiel lorsque les modifications apportées à l'objet attaché sont enregistrées.  
  
 Pour plus d’informations, consultez [Comment : attacher une entité existante au DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Création et modification des liens de relation  
 Lorsque vous ajoutez une nouvelle entité à l’aide la <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> approprié ou méthode *AddTo* méthode de la <xref:System.Data.Services.Client.DataServiceContext> classe qui le **ajouter une référence de Service** génère de la boîte de dialogue, toutes les relations entre la nouvelle entité et les entités associées ne sont pas définies automatiquement.  
  
 Vous pouvez créer et modifier les relations entre des instances d'entité et faire répercuter par la bibliothèque cliente ces modifications dans le service de données. Les relations entre les entités sont définies comme des associations dans le modèle, et <xref:System.Data.Services.Client.DataServiceContext> suit chaque relation comme un objet de lien dans le contexte. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]fournit les méthodes suivantes sur la <xref:System.Data.Services.Client.DataServiceContext> classe pour créer, modifier et supprimer ces liens :  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Crée un lien entre deux objets entité connexes. L'appel de cette méthode revient à appeler <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> et <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> pour créer le nouvel objet et définir la relation avec un objet existant.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Crée un lien entre deux objets entité connexes.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Met à jour un lien existant entre deux objets entité associés. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> est également utilisé pour supprimer des liens avec une cardinalité de zéro-ou-un (`0..1:1`) et un-à-un (`1:1`). Pour ce faire, vous pouvez définir l'objet lié sur `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Marque un lien que le contexte suit pour la suppression lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée. Utilisez cette méthode lorsque vous supprimez un objet connexe ou modifiez une relation en supprimant en premier le lien vers un objet existant et en ajoutant ensuite un lien au nouvel objet connexe.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Notifie le contexte d'un lien existant entre deux objets entité. Le contexte suppose que cette relation existe déjà dans le service de données et ne cherche pas à créer le lien lorsque vous appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Utilisez cette méthode lorsque vous joignez des objets à un contexte et devez joindre également le lien entre les deux. Si vous définissez une nouvelle relation, vous devez utiliser à la place <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Arrête le suivi du lien spécifié dans le contexte. Cette méthode est utilisée pour supprimer les relations un-à-plusieurs (`*:*`). Pour les liens de relation avec une cardinalité de un, vous devez utiliser <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> à la place.|  
  
 L'exemple suivant montre comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> pour ajouter un nouveau `Order_Detail` associé à une entité `Orders` existante. Étant donné que le nouvel objet `Order_Details` est maintenant suivi par <xref:System.Data.Services.Client.DataServiceContext>, la relation de l'objet `Order_Details` ajouté à l'entité `Products` existante est définie par l'appel de la méthode <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> :  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Si la méthode <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> définit des liens qui doivent être créés dans le service de données, pour que ces liens soient répercutés dans les objets du contexte, vous devez également définir les propriétés de navigation sur les objets eux-mêmes. Dans l'exemple précédent, vous devez définir les propriétés de navigation comme suit :  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#setnavprops)]  
  
 Pour plus d’informations, consultez [Comment : définir des relations d’entités](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Enregistrement des modifications  
 Les modifications sont suivies dans l'instance <xref:System.Data.Services.Client.DataServiceContext> mais ne sont pas envoyées au serveur immédiatement. Une fois que vous avez terminé d'effectuer les modifications requises pour une activité spécifiée, appelez <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> afin de soumettre toutes les modifications au service de données. Pour plus d’informations, consultez [gérer le contexte de Service de données](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Vous pouvez également enregistrer des modifications de façon asynchrone à l'aide des méthodes <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> et <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>. Pour plus d’informations, consultez [opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 [Opérations de traitement par lot](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 [Matérialisation d’objet](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [Gérer le contexte de Service de données](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
