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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e92c5d804fca3c04506e951a5c341c89eed1c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="contract"></a><span data-ttu-id="98591-102">Contrat</span><span class="sxs-lookup"><span data-stu-id="98591-102">Contract</span></span>
<span data-ttu-id="98591-103">Contrat</span><span class="sxs-lookup"><span data-stu-id="98591-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98591-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98591-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="98591-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="98591-105">Methods</span></span>  
 <span data-ttu-id="98591-106">La classe Contract ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="98591-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="98591-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="98591-107">Properties</span></span>  
 <span data-ttu-id="98591-108">La classe Contract a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="98591-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="98591-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="98591-109">AppDomainId</span></span>  
 <span data-ttu-id="98591-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="98591-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="98591-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-112">ID du domaine d'application qui héberge le contrat.</span><span class="sxs-lookup"><span data-stu-id="98591-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="98591-113">Comportements</span><span class="sxs-lookup"><span data-stu-id="98591-113">Behaviors</span></span>  
 <span data-ttu-id="98591-114">Type de données : tableau de comportements</span><span class="sxs-lookup"><span data-stu-id="98591-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="98591-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-116">Comportements associés à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="98591-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="98591-117">Nom</span><span class="sxs-lookup"><span data-stu-id="98591-117">Name</span></span>  
 <span data-ttu-id="98591-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98591-118">Data type: string</span></span>  
  
 <span data-ttu-id="98591-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-120">Nom du contrat dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="98591-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="98591-121">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="98591-121">Namespace</span></span>  
 <span data-ttu-id="98591-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98591-122">Data type: string</span></span>  
  
 <span data-ttu-id="98591-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-124">Espace de noms de l'élément `portType` dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="98591-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="98591-125">Opérations</span><span class="sxs-lookup"><span data-stu-id="98591-125">Operations</span></span>  
 <span data-ttu-id="98591-126">Type de données : tableau d'opérations</span><span class="sxs-lookup"><span data-stu-id="98591-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="98591-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-128">Opérations de ce contrat.</span><span class="sxs-lookup"><span data-stu-id="98591-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="98591-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="98591-129">ProcessId</span></span>  
 <span data-ttu-id="98591-130">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="98591-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="98591-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-132">ID du processus qui héberge le contrat.</span><span class="sxs-lookup"><span data-stu-id="98591-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="98591-133">ref</span><span class="sxs-lookup"><span data-stu-id="98591-133">ref</span></span>  
 <span data-ttu-id="98591-134">Type de données: contrat</span><span class="sxs-lookup"><span data-stu-id="98591-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="98591-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-136">Type de rappel lorsque le contrat est un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="98591-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="98591-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="98591-137">SessionMode</span></span>  
 <span data-ttu-id="98591-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98591-138">Data type: string</span></span>  
  
 <span data-ttu-id="98591-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-140">Indique si le contrat nécessite que la liaison associée à ce contrat utilise les sessions de canal.</span><span class="sxs-lookup"><span data-stu-id="98591-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="98591-141">Type</span><span class="sxs-lookup"><span data-stu-id="98591-141">Type</span></span>  
 <span data-ttu-id="98591-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98591-142">Data type: string</span></span>  
  
 <span data-ttu-id="98591-143">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98591-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98591-144">Type du contrat.</span><span class="sxs-lookup"><span data-stu-id="98591-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98591-145">Spécifications</span><span class="sxs-lookup"><span data-stu-id="98591-145">Requirements</span></span>  
  
|<span data-ttu-id="98591-146">MOF</span><span class="sxs-lookup"><span data-stu-id="98591-146">MOF</span></span>|<span data-ttu-id="98591-147">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="98591-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="98591-148">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="98591-148">Namespace</span></span>|<span data-ttu-id="98591-149">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="98591-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98591-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98591-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
