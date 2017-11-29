---
title: "Personnalisation des opérations d'insertion, de mise à jour et de suppression"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e48ac307087d5b90567c720d0c215ac0d52ccb6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="6e5cb-102">Personnalisation des opérations d'insertion, de mise à jour et de suppression</span><span class="sxs-lookup"><span data-stu-id="6e5cb-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="6e5cb-103">Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour implémenter les opérations d'insertion, de lecture, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="6e5cb-104">Dans la pratique toutefois, vous personnalisez généralement votre application en fonction de vos besoins professionnels.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e5cb-105">Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vous permet de personnaliser les opérations d'insertion, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="6e5cb-106">Cette section de rubriques décrit les techniques que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit pour personnaliser les opérations d'insertion, de lecture, de mise à jour et de suppression dans votre application.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e5cb-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6e5cb-107">In This Section</span></span>  
 [<span data-ttu-id="6e5cb-108">Personnalisation d’opérations : vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="6e5cb-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="6e5cb-109">Décrit les différentes techniques fournies par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour personnaliser les opérations d'insertion, de lecture, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="6e5cb-110">INSERT, Update et les opérations de suppression</span><span class="sxs-lookup"><span data-stu-id="6e5cb-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="6e5cb-111">Décrit les processus par défaut de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour manipuler des données de base de données.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="6e5cb-112">Responsabilités du développeur lors de la substitution du comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="6e5cb-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="6e5cb-113">Décrit le rôle du développeur dans l'implémentation des spécifications non appliquées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e5cb-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="6e5cb-114">Ajout d’une logique métier à l’aide de méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="6e5cb-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="6e5cb-115">Explique comment utiliser des méthodes partielles pour substituer des méthodes générées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="6e5cb-115">Describes how to use partial methods to override autogenerated methods.</span></span>
