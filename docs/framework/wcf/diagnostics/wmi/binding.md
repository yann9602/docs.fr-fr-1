---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a><span data-ttu-id="fa2d2-102">Liaison</span><span class="sxs-lookup"><span data-stu-id="fa2d2-102">Binding</span></span>
<span data-ttu-id="fa2d2-103">WMI Binding</span><span class="sxs-lookup"><span data-stu-id="fa2d2-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa2d2-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fa2d2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fa2d2-105">Methods</span></span>  
 <span data-ttu-id="fa2d2-106">La classe Binding ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fa2d2-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fa2d2-107">Properties</span></span>  
 <span data-ttu-id="fa2d2-108">La classe Binding a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa2d2-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="fa2d2-109">BindingElement</span><span class="sxs-lookup"><span data-stu-id="fa2d2-109">BindingElements</span></span>  
 <span data-ttu-id="fa2d2-110">Type de données : tableau BindingElement</span><span class="sxs-lookup"><span data-stu-id="fa2d2-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="fa2d2-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-112">Collection d'éléments de liaison implémentés par la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="fa2d2-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="fa2d2-113">CloseTimeout</span></span>  
 <span data-ttu-id="fa2d2-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="fa2d2-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="fa2d2-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-116">Intervalle de temps spécifié pour l'exécution d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="fa2d2-117">Nom</span><span class="sxs-lookup"><span data-stu-id="fa2d2-117">Name</span></span>  
 <span data-ttu-id="fa2d2-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="fa2d2-118">Data type: string</span></span>  
  
 <span data-ttu-id="fa2d2-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-120">Le nom de la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="fa2d2-121">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="fa2d2-121">Namespace</span></span>  
 <span data-ttu-id="fa2d2-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="fa2d2-122">Data type: string</span></span>  
  
 <span data-ttu-id="fa2d2-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-124">Espace de noms XML de la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="fa2d2-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="fa2d2-125">OpenTimeout</span></span>  
 <span data-ttu-id="fa2d2-126">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="fa2d2-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="fa2d2-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-128">Intervalle de temps spécifié pour l'exécution d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="fa2d2-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fa2d2-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="fa2d2-130">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="fa2d2-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="fa2d2-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-132">Intervalle de temps spécifié pour l'exécution d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="fa2d2-133">Scheme</span><span class="sxs-lookup"><span data-stu-id="fa2d2-133">Scheme</span></span>  
 <span data-ttu-id="fa2d2-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="fa2d2-134">Data type: string</span></span>  
  
 <span data-ttu-id="fa2d2-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-136">Modèle de transport URI utilisé par les fabrications et écouteurs de canal construits par la liaison.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="fa2d2-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="fa2d2-137">SendTimeout</span></span>  
 <span data-ttu-id="fa2d2-138">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="fa2d2-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="fa2d2-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="fa2d2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fa2d2-140">Intervalle de temps spécifié pour l'exécution d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa2d2-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fa2d2-141">Requirements</span></span>  
  
|<span data-ttu-id="fa2d2-142">MOF</span><span class="sxs-lookup"><span data-stu-id="fa2d2-142">MOF</span></span>|<span data-ttu-id="fa2d2-143">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fa2d2-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fa2d2-144">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="fa2d2-144">Namespace</span></span>|<span data-ttu-id="fa2d2-145">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fa2d2-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa2d2-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa2d2-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
