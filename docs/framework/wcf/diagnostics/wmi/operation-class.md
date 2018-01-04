---
title: Operation, classe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54566bc452baa2e02cef7d8d13d29fcd5864c95c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="operation-class"></a><span data-ttu-id="06a54-102">Operation, classe</span><span class="sxs-lookup"><span data-stu-id="06a54-102">Operation class</span></span>
<span data-ttu-id="06a54-103">Opération</span><span class="sxs-lookup"><span data-stu-id="06a54-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06a54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06a54-104">Syntax</span></span>  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="06a54-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="06a54-105">Methods</span></span>  
 <span data-ttu-id="06a54-106">La classe Operation ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="06a54-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="06a54-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="06a54-107">Properties</span></span>  
 <span data-ttu-id="06a54-108">La classe Operation a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="06a54-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="06a54-109">Action</span><span class="sxs-lookup"><span data-stu-id="06a54-109">Action</span></span>  
 <span data-ttu-id="06a54-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="06a54-110">Data type: string</span></span>  
  
 <span data-ttu-id="06a54-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-112">L'action WS-Addressing du message de demande.</span><span class="sxs-lookup"><span data-stu-id="06a54-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="06a54-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="06a54-113">AsyncPattern</span></span>  
 <span data-ttu-id="06a54-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="06a54-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="06a54-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-116">Indique qu’une opération est implémentée à l’aide de façon asynchrone un `Begin`[Ouvrir/fermer les crochets pointus] et `End`paire de méthodes [ouverture/fermeture crochets] dans un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="06a54-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="06a54-117">comportements</span><span class="sxs-lookup"><span data-stu-id="06a54-117">Behaviors</span></span>  
 <span data-ttu-id="06a54-118">Type de données : tableau de comportements</span><span class="sxs-lookup"><span data-stu-id="06a54-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="06a54-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-120">Comportements associés à cette opération.</span><span class="sxs-lookup"><span data-stu-id="06a54-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="06a54-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="06a54-121">IsCallback</span></span>  
 <span data-ttu-id="06a54-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="06a54-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="06a54-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-124">True lorsque l'opération est une opération de rappel.</span><span class="sxs-lookup"><span data-stu-id="06a54-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="06a54-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="06a54-125">IsInitiating</span></span>  
 <span data-ttu-id="06a54-126">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="06a54-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="06a54-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-128">Indique si la méthode implémente une opération qui peut initialiser une session sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="06a54-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="06a54-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="06a54-129">IsOneWay</span></span>  
 <span data-ttu-id="06a54-130">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="06a54-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="06a54-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-132">Indique si une opération retourne un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="06a54-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="06a54-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="06a54-133">IsTerminating</span></span>  
 <span data-ttu-id="06a54-134">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="06a54-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="06a54-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-136">Indique si une opération retourne un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="06a54-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="06a54-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="06a54-137">MethodSignature</span></span>  
 <span data-ttu-id="06a54-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="06a54-138">Data type: string</span></span>  
  
 <span data-ttu-id="06a54-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-140">Signature de méthode de l'opération.</span><span class="sxs-lookup"><span data-stu-id="06a54-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="06a54-141">Name</span><span class="sxs-lookup"><span data-stu-id="06a54-141">Name</span></span>  
 <span data-ttu-id="06a54-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="06a54-142">Data type: string</span></span>  
  
 <span data-ttu-id="06a54-143">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-144">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="06a54-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="06a54-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="06a54-145">ParameterTypes</span></span>  
 <span data-ttu-id="06a54-146">Type de données : tableau de chaînes</span><span class="sxs-lookup"><span data-stu-id="06a54-146">Data type: string array</span></span>  
  
 <span data-ttu-id="06a54-147">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-148">Types des paramètres de l'opération.</span><span class="sxs-lookup"><span data-stu-id="06a54-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="06a54-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="06a54-149">ReplyAction</span></span>  
 <span data-ttu-id="06a54-150">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="06a54-150">Data type: string</span></span>  
  
 <span data-ttu-id="06a54-151">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-152">Valeur de l'action SOAP pour le message de réponse de l'opération.</span><span class="sxs-lookup"><span data-stu-id="06a54-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="06a54-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="06a54-153">ReturnType</span></span>  
 <span data-ttu-id="06a54-154">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="06a54-154">Data type: string</span></span>  
  
 <span data-ttu-id="06a54-155">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="06a54-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="06a54-156">Type de retour de l’opération.</span><span class="sxs-lookup"><span data-stu-id="06a54-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06a54-157">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06a54-157">Requirements</span></span>  
  
|<span data-ttu-id="06a54-158">MOF</span><span class="sxs-lookup"><span data-stu-id="06a54-158">MOF</span></span>|<span data-ttu-id="06a54-159">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="06a54-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="06a54-160">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="06a54-160">Namespace</span></span>|<span data-ttu-id="06a54-161">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="06a54-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06a54-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06a54-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
