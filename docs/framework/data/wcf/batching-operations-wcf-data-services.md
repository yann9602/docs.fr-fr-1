---
title: "Opérations de traitement par lots (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65bf6bfd0bd437848137506605a958f5f2e8d750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="batching-operations-wcf-data-services"></a>Opérations de traitement par lots (services de données WCF)
Le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] du lot prend en charge le traitement des demandes à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-en fonction du service. Pour plus d’informations, consultez [OData : traitement par lot](http://go.microsoft.com/fwlink/?LinkId=186075). Dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], chaque opération qui utilise le <xref:System.Data.Services.Client.DataServiceContext>, tels que l’exécution d’une requête ou d’enregistrer les modifications, les résultats dans une demande distincte qui est envoyé au service de données. Pour maintenir une étendue logique pour les jeux d'opérations, vous pouvez définir explicitement des lots opérationnels. Cela garantit que toutes les opérations dans le lot sont envoyées au service de données dans une requête HTTP unique permet au serveur de traiter les opérations de manière atomique et réduit le nombre d’allers-retours au service de données.  
  
## <a name="batching-query-operations"></a>Opérations de traitement par lot des requêtes  
 Pour exécuter plusieurs requêtes dans un lot unique, vous devez créer chaque requête dans le lot comme une instance distincte de la classe <xref:System.Data.Services.Client.DataServiceRequest%601>. Lorsque vous créez une requête d'interrogation de cette manière, la requête elle-même est définie comme un URI, et elle suit les règles pour l'adressage de ressources. Pour plus d’informations, consultez [accès aux ressources de Service de données](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Les requêtes d'interrogation par lot sont envoyées au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> est appelée qui contient les objets de requête d'interrogation. Cette méthode retourne un objet <xref:System.Data.Services.Client.DataServiceResponse> qui est une collection d'objets <xref:System.Data.Services.Client.QueryOperationResponse%601> qui représentent des réponses aux requêtes individuelles dans le lot, chacune contenant une collection d'objets retournés par la requête ou des informations d'erreur. Lorsqu'une opération de requête unique dans le lot échoue, les informations d'erreur sont retournées dans l'objet <xref:System.Data.Services.Client.QueryOperationResponse%601> pour l'opération qui a échoué et les opérations restantes sont exécutées. Pour plus d’informations, consultez [Comment : exécuter des requêtes dans un lot](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Les requêtes par lot peuvent également être exécutées de façon asynchrone. Pour plus d’informations, consultez [opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Traitement par lot de l'opération SaveChanges  
 Lorsque vous appelez le <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> (méthode), toutes les modifications que le contexte sont traduites en opérations basées sur REST qui sont envoyées en tant que demande la [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service. Par défaut, ces modifications ne sont pas envoyées dans un message de demande unique. Pour exiger que toutes les modifications soient envoyées dans une demande unique, vous devez appeler la <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> (méthode) et inclure une valeur de <xref:System.Data.Services.Client.SaveChangesOptions.Batch> dans le <xref:System.Data.Services.Client.SaveChangesOptions> énumération que vous fournissez à la méthode.  
  
 Vous pouvez également enregistrer de façon asynchrone les modifications par lot. Pour plus d’informations, consultez [opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
