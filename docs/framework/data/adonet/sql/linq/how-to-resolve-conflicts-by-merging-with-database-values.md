---
title: "Comment : résoudre les conflits d'accès concurrentiel en fusionnant des valeurs de base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ee1016a6dc20e58bfafc434617a36f8f8703a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="20b6b-102">Comment : résoudre les conflits d'accès concurrentiel en fusionnant des valeurs de base de données</span><span class="sxs-lookup"><span data-stu-id="20b6b-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="20b6b-103">Pour harmoniser des différences entre des valeurs de base de données attendues et réelles avant de soumettre à nouveau vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.KeepChanges> pour fusionner des valeurs de base de données avec les valeurs de membre client actuelles.</span><span class="sxs-lookup"><span data-stu-id="20b6b-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="20b6b-104">Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="20b6b-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20b6b-105">Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données.</span><span class="sxs-lookup"><span data-stu-id="20b6b-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="20b6b-106">Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="20b6b-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20b6b-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="20b6b-107">Example</span></span>  
 <span data-ttu-id="20b6b-108">Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications car User2 a modifié entre-temps les colonnes Assistant et Department.</span><span class="sxs-lookup"><span data-stu-id="20b6b-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="20b6b-109">Le tableau suivant présente la situation.</span><span class="sxs-lookup"><span data-stu-id="20b6b-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="20b6b-110">Manager</span><span class="sxs-lookup"><span data-stu-id="20b6b-110">Manager</span></span>|<span data-ttu-id="20b6b-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="20b6b-111">Assistant</span></span>|<span data-ttu-id="20b6b-112">Department</span><span class="sxs-lookup"><span data-stu-id="20b6b-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="20b6b-113">État de la base de données d'origine lors d'une interrogation par User1 et User2.</span><span class="sxs-lookup"><span data-stu-id="20b6b-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="20b6b-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="20b6b-114">Alfreds</span></span>|<span data-ttu-id="20b6b-115">Maria</span><span class="sxs-lookup"><span data-stu-id="20b6b-115">Maria</span></span>|<span data-ttu-id="20b6b-116">Sales</span><span class="sxs-lookup"><span data-stu-id="20b6b-116">Sales</span></span>|  
|<span data-ttu-id="20b6b-117">User1 s'apprête à soumettre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="20b6b-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="20b6b-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="20b6b-118">Alfred</span></span>||<span data-ttu-id="20b6b-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="20b6b-119">Marketing</span></span>|  
|<span data-ttu-id="20b6b-120">User2 a déjà soumis ces modifications.</span><span class="sxs-lookup"><span data-stu-id="20b6b-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="20b6b-121">Mary</span><span class="sxs-lookup"><span data-stu-id="20b6b-121">Mary</span></span>|<span data-ttu-id="20b6b-122">Service</span><span class="sxs-lookup"><span data-stu-id="20b6b-122">Service</span></span>|  
  
 <span data-ttu-id="20b6b-123">User1 décide de résoudre ce conflit en fusionnant des valeurs de base de données avec les valeurs de membre client actuelles.</span><span class="sxs-lookup"><span data-stu-id="20b6b-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="20b6b-124">Les valeurs de base de données seront donc remplacées uniquement lorsque l'ensemble de modifications actuel aura également modifié cette valeur.</span><span class="sxs-lookup"><span data-stu-id="20b6b-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="20b6b-125">Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.KeepChanges>, le résultat dans la base de données se présente comme dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="20b6b-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="20b6b-126">Manager</span><span class="sxs-lookup"><span data-stu-id="20b6b-126">Manager</span></span>|<span data-ttu-id="20b6b-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="20b6b-127">Assistant</span></span>|<span data-ttu-id="20b6b-128">Department</span><span class="sxs-lookup"><span data-stu-id="20b6b-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="20b6b-129">Nouvel état après résolution du conflit.</span><span class="sxs-lookup"><span data-stu-id="20b6b-129">New state after conflict resolution.</span></span>|<span data-ttu-id="20b6b-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="20b6b-130">Alfred</span></span><br /><br /> <span data-ttu-id="20b6b-131">(de User1)</span><span class="sxs-lookup"><span data-stu-id="20b6b-131">(from User1)</span></span>|<span data-ttu-id="20b6b-132">Mary</span><span class="sxs-lookup"><span data-stu-id="20b6b-132">Mary</span></span><br /><br /> <span data-ttu-id="20b6b-133">(de User2)</span><span class="sxs-lookup"><span data-stu-id="20b6b-133">(from User2)</span></span>|<span data-ttu-id="20b6b-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="20b6b-134">Marketing</span></span><br /><br /> <span data-ttu-id="20b6b-135">(de User1)</span><span class="sxs-lookup"><span data-stu-id="20b6b-135">(from User1)</span></span>|  
  
 <span data-ttu-id="20b6b-136">L'exemple suivant montre comment fusionner des valeurs de base de données avec les valeurs de membre client actuelles (à moins que le client ait également modifié cette valeur).</span><span class="sxs-lookup"><span data-stu-id="20b6b-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="20b6b-137">Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.</span><span class="sxs-lookup"><span data-stu-id="20b6b-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="20b6b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20b6b-138">See Also</span></span>  
 [<span data-ttu-id="20b6b-139">Guide pratique pour résoudre des conflits en remplaçant des valeurs de bases de données</span><span class="sxs-lookup"><span data-stu-id="20b6b-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [<span data-ttu-id="20b6b-140">Guide pratique pour résoudre des conflits en conservant des valeurs de bases de données</span><span class="sxs-lookup"><span data-stu-id="20b6b-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [<span data-ttu-id="20b6b-141">Guide pratique pour gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="20b6b-141">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
