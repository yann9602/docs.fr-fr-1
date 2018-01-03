---
title: "Comment : exécuter les requêtes de services de données asynchrones (services de données WCF)"
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
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfffd8405411327d0c31510850ceaa389bdc2d72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Comment : exécuter les requêtes de services de données asynchrones (services de données WCF)
En utilisant les bibliothèques clientes [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez effectuer de façon asynchrone des opérations client-serveur, telles que l'exécution de requêtes et l'enregistrement de modifications. Pour plus d’informations, consultez [opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  Dans une application où le rappel doit être appelé sur un thread spécifique, vous devez marshaler explicitement l'exécution de la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>. Pour plus d’informations, consultez [opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment exécuter une requête asynchrone en appelant la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> pour démarrer la requête. Le délégué inline delegate appelle la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pour afficher les résultats de la requête.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
