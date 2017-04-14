---
title: "Comment&#160;: appeler des op&#233;rations de service WCF de fa&#231;on asynchrone | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Comment&#160;: appeler des op&#233;rations de service WCF de fa&#231;on asynchrone
Cette rubrique présente comment un client peut accéder de façon asynchrone à une opération de service.Le service dans cette rubrique implémente l'interface `ICalculator`.Le client peut appeler les opérations sur cette interface de manière asynchrone à l'aide du modèle d'appel asynchrone commandé par événement.\(Pour plus d'informations sur le modèle d'appel asynchrone basé sur des événements, consultez [Programmation multithread avec le modèle asynchrone basé sur des événements](http://go.microsoft.com/fwlink/?LinkId=248184)\).Pour obtenir un exemple illustrant comment implémenter une opération de façon asynchrone dans un service, consultez [Comment : implémenter une opération de service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).Pour plus d'informations sur les opérations synchrones et asynchrones, consultez [Opérations synchrones et asynchrones](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Le modèle d'appel asynchrone commandé par événement n'est pas pris en charge lorsqu'il utilise un <xref:System.ServiceModel.ChannelFactory%601>.Pour plus d'informations sur les appels asynchrones à l'aide de <xref:System.ServiceModel.ChannelFactory%601>, consultez [Comment : appeler des opérations de façon asynchrone à l'aide d'une fabrication de canal](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## Procédure  
  
#### Pour appeler des opérations de service WCF de façon asynchrone  
  
1.  Exécutez l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) en définissant les deux options `/async` et `/tcv:Version35` comme illustré dans la commande suivante.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Cette opération génère en plus des opérations asynchrones basées sur les délégués standard et des opérations synchrones, un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui contient :  
  
    -   Deux opérations \<`operationName`\>`Async` destinées à l'approche de l'appel asynchrone basé sur les événements.Par exemple :  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Les événements terminés d'opérations de la forme \<`operationName`\>`Completed` destinés à l'approche de l'appel asynchrone basé sur les événements.Par exemple :  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   Les types <xref:System.EventArgs?displayProperty=fullName> pour chaque opération \(de la forme \<`operationName`\>`CompletedEventArgs`\) destinés à l'approche de l'appel asynchrone basé sur les événements.Par exemple :  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  Dans l'application d'appel, créez une méthode de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Avant d'appeler l'opération, utilisez un nouveau <xref:System.EventHandler%601?displayProperty=fullName> générique de type \<`operationName`\>`EventArgs` pour ajouter la méthode de gestionnaire d'événements \(créée à l'étape précédente\) à l'événement \<`operationName`\>`Completed`.Ensuite, appelez la méthode \<`operationName`\>`Async`.Par exemple :  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## Exemple  
  
> [!NOTE]
>  Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>. Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`.Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## Voir aussi  
 [Comment : implémenter une opération de service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)