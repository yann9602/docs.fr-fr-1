---
title: "Comment : résoudre des conflits en conservant des valeurs de bases de données"
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
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0747a4318fdab76c5fbd920f7291346d4d8ff58d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="db723-102">Comment : résoudre des conflits en conservant des valeurs de bases de données</span><span class="sxs-lookup"><span data-stu-id="db723-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="db723-103">Pour harmoniser les différences entre les valeurs de base de données attendues et réelles avant d'essayer de renvoyer vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> pour conserver les valeurs trouvées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="db723-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="db723-104">Les valeurs actuelles dans le modèle objet sont alors remplacées.</span><span class="sxs-lookup"><span data-stu-id="db723-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="db723-105">Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="db723-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db723-106">Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données.</span><span class="sxs-lookup"><span data-stu-id="db723-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="db723-107">Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="db723-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db723-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="db723-108">Example</span></span>  
 <span data-ttu-id="db723-109">Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications car User2 a modifié entre-temps les colonnes Assistant et Department.</span><span class="sxs-lookup"><span data-stu-id="db723-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="db723-110">Le tableau suivant présente la situation.</span><span class="sxs-lookup"><span data-stu-id="db723-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="db723-111">Manager</span><span class="sxs-lookup"><span data-stu-id="db723-111">Manager</span></span>|<span data-ttu-id="db723-112">Assistant</span><span class="sxs-lookup"><span data-stu-id="db723-112">Assistant</span></span>|<span data-ttu-id="db723-113">Department</span><span class="sxs-lookup"><span data-stu-id="db723-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="db723-114">État de la base de données d'origine lors d'une interrogation par User1 et User2.</span><span class="sxs-lookup"><span data-stu-id="db723-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="db723-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="db723-115">Alfreds</span></span>|<span data-ttu-id="db723-116">Maria</span><span class="sxs-lookup"><span data-stu-id="db723-116">Maria</span></span>|<span data-ttu-id="db723-117">Sales</span><span class="sxs-lookup"><span data-stu-id="db723-117">Sales</span></span>|  
|<span data-ttu-id="db723-118">User1 s'apprête à soumettre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="db723-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="db723-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="db723-119">Alfred</span></span>||<span data-ttu-id="db723-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="db723-120">Marketing</span></span>|  
|<span data-ttu-id="db723-121">User2 a déjà soumis ces modifications.</span><span class="sxs-lookup"><span data-stu-id="db723-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="db723-122">Mary</span><span class="sxs-lookup"><span data-stu-id="db723-122">Mary</span></span>|<span data-ttu-id="db723-123">Service</span><span class="sxs-lookup"><span data-stu-id="db723-123">Service</span></span>|  
  
 <span data-ttu-id="db723-124">User1 décide de résoudre ce conflit en remplaçant les valeurs actuelles dans le modèle objet par les valeurs de base de données les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="db723-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="db723-125">Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, le résultat dans la base de données se présente comme dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="db723-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="db723-126">Manager</span><span class="sxs-lookup"><span data-stu-id="db723-126">Manager</span></span>|<span data-ttu-id="db723-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="db723-127">Assistant</span></span>|<span data-ttu-id="db723-128">Department</span><span class="sxs-lookup"><span data-stu-id="db723-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="db723-129">Nouvel état après résolution du conflit.</span><span class="sxs-lookup"><span data-stu-id="db723-129">New state after conflict resolution.</span></span>|<span data-ttu-id="db723-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="db723-130">Alfreds</span></span><br /><br /> <span data-ttu-id="db723-131">(d'origine)</span><span class="sxs-lookup"><span data-stu-id="db723-131">(original)</span></span>|<span data-ttu-id="db723-132">Mary</span><span class="sxs-lookup"><span data-stu-id="db723-132">Mary</span></span><br /><br /> <span data-ttu-id="db723-133">(de User2)</span><span class="sxs-lookup"><span data-stu-id="db723-133">(from User2)</span></span>|<span data-ttu-id="db723-134">Service</span><span class="sxs-lookup"><span data-stu-id="db723-134">Service</span></span><br /><br /> <span data-ttu-id="db723-135">(de User2)</span><span class="sxs-lookup"><span data-stu-id="db723-135">(from User2)</span></span>|  
  
 <span data-ttu-id="db723-136">Le code d'exemple suivant indique comment remplacer les valeurs actuelles dans le modèle objet par les valeurs de base de données.</span><span class="sxs-lookup"><span data-stu-id="db723-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="db723-137">Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.</span><span class="sxs-lookup"><span data-stu-id="db723-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="db723-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db723-138">See Also</span></span>  
 [<span data-ttu-id="db723-139">Guide pratique pour gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="db723-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
