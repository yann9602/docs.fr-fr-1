---
title: "Personnalisation d'opérations : vue d'ensemble"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6d3491ccd183224063c435f6b377f60b175d5383
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="ddb96-102">Personnalisation d'opérations : vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ddb96-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="ddb96-103">Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour les opérations d'insertion, de mise à jour et de suppression selon le mappage.</span><span class="sxs-lookup"><span data-stu-id="ddb96-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="ddb96-104">Dans la pratique cependant, vous souhaiterez généralement ajouter votre propre logique métier pour des raisons de sécurité, de validation, etc.</span><span class="sxs-lookup"><span data-stu-id="ddb96-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ddb96-105">techniques de personnalisation de ces opérations sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="ddb96-105"> techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="ddb96-106">Options de chargement</span><span class="sxs-lookup"><span data-stu-id="ddb96-106">Loading Options</span></span>  
 <span data-ttu-id="ddb96-107">Dans vos requêtes, vous pouvez déterminer quelle quantité de données liées à votre cible principale est récupérée lorsque vous vous connectez à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ddb96-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="ddb96-108">Cette fonctionnalité est implémentée en grande partie à l'aide de <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="ddb96-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="ddb96-109">Pour plus d’informations, consultez [différée / chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="ddb96-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="ddb96-110">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="ddb96-110">Partial Methods</span></span>  
 <span data-ttu-id="ddb96-111">Dans son mappage par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des méthodes partielles qui vous permettent d'implémenter votre logique métier.</span><span class="sxs-lookup"><span data-stu-id="ddb96-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="ddb96-112">Pour plus d’informations, consultez [Ajout d’entreprise logique par à l’aide de méthodes partielles](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ddb96-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="ddb96-113">Procédures stockées et fonctions définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ddb96-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ddb96-114">prend en charge l’utilisation de procédures stockées et fonctions définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ddb96-114"> supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="ddb96-115">Les procédures stockées sont couramment utilisées pour personnaliser des opérations.</span><span class="sxs-lookup"><span data-stu-id="ddb96-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="ddb96-116">Pour plus d’informations, consultez [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ddb96-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb96-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb96-117">See Also</span></span>  
 [<span data-ttu-id="ddb96-118">Personnalisation des opérations d’insertion, de mise à jour et de suppression</span><span class="sxs-lookup"><span data-stu-id="ddb96-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
