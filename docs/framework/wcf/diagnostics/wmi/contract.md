---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a5cb87b9ed61fd278ce0f2e05e5f1c954de5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="contract"></a><span data-ttu-id="5d178-102">Contrat</span><span class="sxs-lookup"><span data-stu-id="5d178-102">Contract</span></span>
<span data-ttu-id="5d178-103">Contrat</span><span class="sxs-lookup"><span data-stu-id="5d178-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d178-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d178-104">Syntax</span></span>  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5d178-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5d178-105">Methods</span></span>  
 <span data-ttu-id="5d178-106">La classe Contract ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="5d178-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d178-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5d178-107">Properties</span></span>  
 <span data-ttu-id="5d178-108">La classe Contract a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d178-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="5d178-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="5d178-109">AppDomainId</span></span>  
 <span data-ttu-id="5d178-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="5d178-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="5d178-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-112">ID du domaine d'application qui héberge le contrat.</span><span class="sxs-lookup"><span data-stu-id="5d178-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="5d178-113">Comportements</span><span class="sxs-lookup"><span data-stu-id="5d178-113">Behaviors</span></span>  
 <span data-ttu-id="5d178-114">Type de données : tableau de comportements</span><span class="sxs-lookup"><span data-stu-id="5d178-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="5d178-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-116">Comportements associés à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="5d178-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="5d178-117">Name</span><span class="sxs-lookup"><span data-stu-id="5d178-117">Name</span></span>  
 <span data-ttu-id="5d178-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5d178-118">Data type: string</span></span>  
  
 <span data-ttu-id="5d178-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-120">Nom du contrat dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="5d178-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="5d178-121">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5d178-121">Namespace</span></span>  
 <span data-ttu-id="5d178-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5d178-122">Data type: string</span></span>  
  
 <span data-ttu-id="5d178-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-124">Espace de noms de l'élément `portType` dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="5d178-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="5d178-125">Opérations</span><span class="sxs-lookup"><span data-stu-id="5d178-125">Operations</span></span>  
 <span data-ttu-id="5d178-126">Type de données : tableau d'opérations</span><span class="sxs-lookup"><span data-stu-id="5d178-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="5d178-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-128">Opérations de ce contrat.</span><span class="sxs-lookup"><span data-stu-id="5d178-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="5d178-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="5d178-129">ProcessId</span></span>  
 <span data-ttu-id="5d178-130">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="5d178-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="5d178-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-132">ID du processus qui héberge le contrat.</span><span class="sxs-lookup"><span data-stu-id="5d178-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="5d178-133">ref</span><span class="sxs-lookup"><span data-stu-id="5d178-133">ref</span></span>  
 <span data-ttu-id="5d178-134">Type de données: contrat</span><span class="sxs-lookup"><span data-stu-id="5d178-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="5d178-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-136">Type de rappel lorsque le contrat est un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="5d178-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="5d178-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="5d178-137">SessionMode</span></span>  
 <span data-ttu-id="5d178-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5d178-138">Data type: string</span></span>  
  
 <span data-ttu-id="5d178-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-140">Indique si le contrat nécessite que la liaison associée à ce contrat utilise les sessions de canal.</span><span class="sxs-lookup"><span data-stu-id="5d178-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="5d178-141">Type</span><span class="sxs-lookup"><span data-stu-id="5d178-141">Type</span></span>  
 <span data-ttu-id="5d178-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5d178-142">Data type: string</span></span>  
  
 <span data-ttu-id="5d178-143">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5d178-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d178-144">Type du contrat.</span><span class="sxs-lookup"><span data-stu-id="5d178-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d178-145">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d178-145">Requirements</span></span>  
  
|<span data-ttu-id="5d178-146">MOF</span><span class="sxs-lookup"><span data-stu-id="5d178-146">MOF</span></span>|<span data-ttu-id="5d178-147">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5d178-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5d178-148">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5d178-148">Namespace</span></span>|<span data-ttu-id="5d178-149">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5d178-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d178-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d178-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
