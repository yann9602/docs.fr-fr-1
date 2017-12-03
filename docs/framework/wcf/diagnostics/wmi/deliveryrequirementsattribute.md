---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="5322b-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="5322b-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="5322b-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="5322b-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5322b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5322b-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5322b-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5322b-105">Methods</span></span>  
 <span data-ttu-id="5322b-106">La classe DeliveryRequirementsAttribute ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="5322b-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5322b-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5322b-107">Properties</span></span>  
 <span data-ttu-id="5322b-108">La classe DeliveryRequirementsAttribute a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5322b-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="5322b-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="5322b-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="5322b-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5322b-110">Data type: string</span></span>  
  
 <span data-ttu-id="5322b-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5322b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5322b-112">Spécifie si la liaison pour un service prend en charge des contrats.</span><span class="sxs-lookup"><span data-stu-id="5322b-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="5322b-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="5322b-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="5322b-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="5322b-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="5322b-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5322b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5322b-116">Spécifie si la liaison prend en charge les messages ordonnés.</span><span class="sxs-lookup"><span data-stu-id="5322b-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="5322b-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="5322b-117">TargetContract</span></span>  
 <span data-ttu-id="5322b-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5322b-118">Data type: string</span></span>  
  
 <span data-ttu-id="5322b-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5322b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5322b-120">Contrat auquel il s'applique.</span><span class="sxs-lookup"><span data-stu-id="5322b-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5322b-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5322b-121">Requirements</span></span>  
  
|<span data-ttu-id="5322b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="5322b-122">MOF</span></span>|<span data-ttu-id="5322b-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5322b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5322b-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5322b-124">Namespace</span></span>|<span data-ttu-id="5322b-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5322b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5322b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5322b-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
