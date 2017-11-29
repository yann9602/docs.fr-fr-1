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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7606aeeeb3e2e583f9a217b78bcae4aebc6d8662
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="cc764-102">Gestion des erreurs dans les activités asynchrones</span><span class="sxs-lookup"><span data-stu-id="cc764-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="cc764-103">Le fait de fournir la gestion des erreurs dans <xref:System.Activities.AsyncCodeActivity> implique le routage de l'erreur via le système de rappel de l'activité.</span><span class="sxs-lookup"><span data-stu-id="cc764-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="cc764-104">Cette rubrique décrit comment obtenir une erreur résultant d'une opération asynchrone vers l'hôte, à l'aide de l'exemple d'activité de SendMail.</span><span class="sxs-lookup"><span data-stu-id="cc764-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="cc764-105">Retourne une erreur résultant d'une activité asynchrone à l'hôte</span><span class="sxs-lookup"><span data-stu-id="cc764-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="cc764-106">Router une erreur d'opération asynchrone vers l'hôte dans l'exemple d'activité de SendMail implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc764-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="cc764-107">Ajoutez une propriété Exception à la classe `SendMailAsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="cc764-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="cc764-108">Copiez l'erreur levée dans cette propriété dans le gestionnaire d'événements `SendCompleted`.</span><span class="sxs-lookup"><span data-stu-id="cc764-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="cc764-109">Lève l'exception dans le gestionnaire d'événements `EndExecute`.</span><span class="sxs-lookup"><span data-stu-id="cc764-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="cc764-110">Le code obtenu se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="cc764-110">The resulting code is as follows.</span></span>  
  
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
