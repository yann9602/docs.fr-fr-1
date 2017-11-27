---
title: "Apport et soumission de modifications de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb52916e8e0948725a2eeb15cf78410077c7dca1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="9b67d-102">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="9b67d-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="9b67d-103">Les rubriques de cette section décrivent comment effectuer et transmettre des modifications à la base de données et comment gérer des conflits d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="9b67d-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b67d-104">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="9b67d-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9b67d-105">Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9b67d-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="9b67d-106">Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent développer des procédures stockées dans le même but à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9b67d-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b67d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9b67d-107">In This Section</span></span>  
 [<span data-ttu-id="9b67d-108">Comment : insérer des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="9b67d-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="9b67d-109">Explique comment insérer des lignes dans la base de données en ajoutant des objets au modèle objet.</span><span class="sxs-lookup"><span data-stu-id="9b67d-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="9b67d-110">Comment : mettre à jour dans la base de données</span><span class="sxs-lookup"><span data-stu-id="9b67d-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="9b67d-111">Explique comment mettre à jour des lignes dans la base de données en mettant à jour des objets du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="9b67d-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="9b67d-112">Comment : supprimer des lignes de la base de données</span><span class="sxs-lookup"><span data-stu-id="9b67d-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="9b67d-113">Explique comment supprimer des lignes de la base de données en supprimant des objets du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="9b67d-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="9b67d-114">Comment : soumettre des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="9b67d-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="9b67d-115">Explique comment envoyer des modifications de modèle objet à la base de données.</span><span class="sxs-lookup"><span data-stu-id="9b67d-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="9b67d-116">Comment : mettre entre les envois de données à l’aide de Transactions</span><span class="sxs-lookup"><span data-stu-id="9b67d-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="9b67d-117">Explique comment inclure des opérations dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="9b67d-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="9b67d-118">Comment : créer dynamiquement une base de données</span><span class="sxs-lookup"><span data-stu-id="9b67d-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="9b67d-119">Explique comment générer dynamiquement des bases de données et des scénarios classiques pour cette approche.</span><span class="sxs-lookup"><span data-stu-id="9b67d-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="9b67d-120">Comment : gérer les conflits de modifications</span><span class="sxs-lookup"><span data-stu-id="9b67d-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="9b67d-121">Propose des techniques pour traiter les problèmes d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="9b67d-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
