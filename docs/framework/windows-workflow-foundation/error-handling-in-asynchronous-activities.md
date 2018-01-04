---
title: "Gestion des erreurs dans les activités asynchrones"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75136ec44618ed23bab1e7f9761c23664dc3f300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="error-handling-in-asynchronous-activities"></a>Gestion des erreurs dans les activités asynchrones
Le fait de fournir la gestion des erreurs dans <xref:System.Activities.AsyncCodeActivity> implique le routage de l'erreur via le système de rappel de l'activité. Cette rubrique décrit comment obtenir une erreur résultant d'une opération asynchrone vers l'hôte, à l'aide de l'exemple d'activité de SendMail.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Retourne une erreur résultant d'une activité asynchrone à l'hôte  
 Router une erreur d'opération asynchrone vers l'hôte dans l'exemple d'activité de SendMail implique les étapes suivantes :  
  
-   Ajoutez une propriété Exception à la classe `SendMailAsyncResult`.  
  
-   Copiez l'erreur levée dans cette propriété dans le gestionnaire d'événements `SendCompleted`.  
  
-   Lève l'exception dans le gestionnaire d'événements `EndExecute`.  
  
 Le code obtenu se présente comme suit :  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }   
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;   
        }  
    }  
```
