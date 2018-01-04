---
title: "Comment : appeler des opérations de service WCF de façon asynchrone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f8a22a5a5b9f388cdfb7b5e5edfa0a54b628aa0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Comment : appeler des opérations de service WCF de façon asynchrone
Cette rubrique présente comment un client peut accéder de façon asynchrone à une opération de service. Le service dans cette rubrique implémente l'interface `ICalculator`. Le client peut appeler les opérations sur cette interface de manière asynchrone à l'aide du modèle d'appel asynchrone commandé par événement. (Pour plus d’informations sur le modèle d’appel asynchrone basé sur des événements, consultez [programmation multithread avec le modèle asynchrone basé sur événement](http://go.microsoft.com/fwlink/?LinkId=248184)). Pour obtenir un exemple qui montre comment implémenter une opération de façon asynchrone dans un service, consultez [Comment : implémenter une opération de Service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [synchrone et asynchrone des opérations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Le modèle d'appel asynchrone commandé par événement n'est pas pris en charge lorsqu'il utilise un <xref:System.ServiceModel.ChannelFactory%601>. Pour plus d’informations sur les appels asynchrones à l’aide de la <xref:System.ServiceModel.ChannelFactory%601>, consultez [Comment : appeler opérations de façon asynchrone en utilisant une fabrique de canaux](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Pour appeler des opérations de service WCF de façon asynchrone  
  
1.  Exécuter la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil à la fois avec la `/async` et le `/tcv:Version35` commande options ensemble, comme indiqué dans la commande suivante.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Cette opération génère en plus des opérations asynchrones basées sur les délégués standard et des opérations synchrones, un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui contient :  
  
    -   Deux <`operationName` > `Async` operations pour une utilisation avec l’approche appel asynchrone basé sur des événements. Exemple :  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Événements d’opération s’est terminée sous la forme <`operationName` > `Completed` pour une utilisation avec l’approche appel asynchrone basé sur des événements. Exemple :  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType>types pour chaque opération (sous la forme <`operationName`>`CompletedEventArgs`) pour une utilisation avec l’approche appel asynchrone basé sur des événements. Exemple :  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  Dans l'application d'appel, créez une méthode de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Avant d’appeler l’opération, utilisez un nouveau générique <xref:System.EventHandler%601?displayProperty=nameWithType> de type <`operationName` > `EventArgs` pour ajouter la méthode de gestionnaire (créée à l’étape précédente) à la <`operationName` > `Completed` événement. Appelez ensuite la <`operationName` > `Async` (méthode). Exemple :  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Exemple  
  
> [!NOTE]
>  Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>. Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>. Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`. Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>. Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour implémenter une opération de service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
