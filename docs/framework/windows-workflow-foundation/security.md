---
title: "Sécurité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0063497bc500a11d59dd88e0cb7d738d5c4bb6e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="security"></a><span data-ttu-id="09656-102">Sécurité</span><span class="sxs-lookup"><span data-stu-id="09656-102">Security</span></span>
<span data-ttu-id="09656-103">Le magasin d'instances de workflow SQL utilise les rôles de sécurité de base de données suivants pour sécuriser l'accès aux informations d'état de l'instance dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="09656-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="09656-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="09656-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="09656-105">Ce rôle dispose d'un accès en lecture et en écriture aux vues publiques et de droits d'exécution sur les procédures stockées impliquées dans la création, le chargement et l'enregistrement des instances.</span><span class="sxs-lookup"><span data-stu-id="09656-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="09656-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="09656-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="09656-107">Ce rôle dispose d'un accès en lecture seule aux vues publiques.</span><span class="sxs-lookup"><span data-stu-id="09656-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="09656-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="09656-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="09656-109">Ce rôle a des droits d'exécution aux procédures stockées impliquées dans le processus de l'activation de l'instance.</span><span class="sxs-lookup"><span data-stu-id="09656-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="09656-110">Pour plus d’informations sur l’activation de l’instance, consultez [activation d’Instance](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="09656-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="09656-111">Le compte d'utilisateur sous lequel un hôte générique (tel que le service de gestion du flux de travail de [!INCLUDE[dublin](../../../includes/dublin-md.md)]) doit être ajouté à ce rôle de base de données.</span><span class="sxs-lookup"><span data-stu-id="09656-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="09656-112">sécurité pour les magasins de persistance avec Windows Server AppFabric, consultez [Configuration de la sécurité pour les magasins de persistance dans AppFabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="09656-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="09656-113">Un client qui a accès à ses propres données d'instance dans le magasin d'instances a accès à toutes les autres instances dans le même magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="09656-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="09656-114">Le magasin d'instances ne prend pas en charge les autorisations de sécurité au niveau de l'instance.</span><span class="sxs-lookup"><span data-stu-id="09656-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="09656-115">Vous devez créer des magasins d'instances distincts et mapper des groupes/utilisateurs différents pour avoir accès aux différents magasins.</span><span class="sxs-lookup"><span data-stu-id="09656-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
