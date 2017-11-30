---
title: Transactions2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c7611ce26c1a3b9150a60ced7b4931cc1282eecd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transactions"></a><span data-ttu-id="c8bda-102">Transactions</span><span class="sxs-lookup"><span data-stu-id="c8bda-102">Transactions</span></span>
<span data-ttu-id="c8bda-103">Cette section contient des exemples qui illustrent des transactions de workflow dans [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8bda-103">This section contains samples that demonstrate workflow transactions in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8bda-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c8bda-104">In This Section</span></span>  
 [<span data-ttu-id="c8bda-105">Bases de TransactionScope</span><span class="sxs-lookup"><span data-stu-id="c8bda-105">Basic TransactionScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 <span data-ttu-id="c8bda-106">Est composé de quatre scénarios qui montrent comment imbriquer des instances <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="c8bda-106">Consists of four scenarios that show how to nest <xref:System.Activities.Statements.TransactionScope> instances.</span></span>  
  
 [<span data-ttu-id="c8bda-107">Utilisation de TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="c8bda-107">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 <span data-ttu-id="c8bda-108">Montre comment passer une transaction d'un client à un serveur à l'aide de <xref:System.Activities.Statements.TransactionScope> pour créer une nouvelle transaction sur le client et un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour recevoir un message avec une transaction passée et étendre la durée de vie de la transaction sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="c8bda-108">Demonstrates how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span>  
  
 [<span data-ttu-id="c8bda-109">Imbrication de TransactionScope dans un service</span><span class="sxs-lookup"><span data-stu-id="c8bda-109">Nesting of TransactionScope within a service</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 <span data-ttu-id="c8bda-110">Est composé de deux scénarios qui montrent comment gérer des instances d'activité <xref:System.Activities.Statements.TransactionScope> dans un service.</span><span class="sxs-lookup"><span data-stu-id="c8bda-110">Consists of two scenarios that show how to handle <xref:System.Activities.Statements.TransactionScope> activity instances within a service.</span></span>
