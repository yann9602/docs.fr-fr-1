---
title: Exceptions, transactions et compensation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be803580a4d8ed195222e5960cfa6e26804d91c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="b93a8-102">Exceptions, transactions et compensation</span><span class="sxs-lookup"><span data-stu-id="b93a8-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="b93a8-103"> fournit plusieurs mécanismes différents pour gérer les conditions d'erreur d'exécution dans les workflows.</span><span class="sxs-lookup"><span data-stu-id="b93a8-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="b93a8-104">Les workflows peuvent utiliser une combinaison de gestionnaires d’exceptions, transactions, annulation et compensation pour gérer et effectuer une récupération normale à partir des conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b93a8-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b93a8-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b93a8-105">In This Section</span></span>  
 [<span data-ttu-id="b93a8-106">Exceptions</span><span class="sxs-lookup"><span data-stu-id="b93a8-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="b93a8-107">Montre comment utiliser l'activité <xref:System.Activities.Statements.TryCatch> pour gérer des exceptions dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="b93a8-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="b93a8-108">Transactions</span><span class="sxs-lookup"><span data-stu-id="b93a8-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="b93a8-109">Montre comment utiliser l'activité <xref:System.Activities.Statements.TransactionScope> pour utiliser des transactions dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="b93a8-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="b93a8-110">Compensation</span><span class="sxs-lookup"><span data-stu-id="b93a8-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="b93a8-111">Décrit la compensation dans les workflows et montre comment utiliser des activités de compensation telles que <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate> et <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="b93a8-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="b93a8-112">Annulation</span><span class="sxs-lookup"><span data-stu-id="b93a8-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="b93a8-113">Explique comment effectuer la gestion des annulations dans les workflows à l'aide d'activités intégrées ainsi que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b93a8-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="b93a8-114">Débogage de workflows</span><span class="sxs-lookup"><span data-stu-id="b93a8-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="b93a8-115">Décrit comment déboguer des workflows.</span><span class="sxs-lookup"><span data-stu-id="b93a8-115">Describes how to debug workflows.</span></span>
