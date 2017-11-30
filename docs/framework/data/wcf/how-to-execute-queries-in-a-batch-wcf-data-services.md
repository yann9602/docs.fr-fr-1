---
title: "Comment : exécuter les requêtes dans un lot (services de données WCF)"
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
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d868881a3ff5c79f1f003881f58c726ebf25385e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Comment : exécuter les requêtes dans un lot (services de données WCF)
À l’aide de la [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliothèque cliente, vous pouvez exécuter plusieurs requêtes sur le service de données dans un lot unique. Pour plus d’informations, consultez [opérations de traitement par lot](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> pour exécuter un tableau d'objets <xref:System.Data.Services.Client.DataServiceRequest%601> qui contient des requêtes qui retournent des objets `Customers` et `Products` du service de données Northwind. La collection d'objets <xref:System.Data.Services.Client.QueryOperationResponse%601> dans le <xref:System.Data.Services.Client.DataServiceResponse> retourné est énumérée, et la collection d'objets contenue dans chaque <xref:System.Data.Services.Client.QueryOperationResponse%601> est également énumérée.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
