---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adac65808853ec75e37245c8c9fa031a533c22a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="378b2-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="378b2-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="378b2-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="378b2-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="378b2-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="378b2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="378b2-105">Methods</span></span>  
 <span data-ttu-id="378b2-106">La classe BinaryMessageEncodingBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="378b2-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="378b2-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="378b2-107">Properties</span></span>  
 <span data-ttu-id="378b2-108">La classe BinaryMessageEncodingBindingElement a les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="378b2-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="378b2-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="378b2-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="378b2-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="378b2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="378b2-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="378b2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="378b2-112">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="378b2-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="378b2-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="378b2-113">MaxSessionSize</span></span>  
 <span data-ttu-id="378b2-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="378b2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="378b2-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="378b2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="378b2-116">Valeur qui spécifie la taille, en octets, de la mémoire tampon utilisée pour l'encodage.</span><span class="sxs-lookup"><span data-stu-id="378b2-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="378b2-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="378b2-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="378b2-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="378b2-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="378b2-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="378b2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="378b2-120">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="378b2-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="378b2-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="378b2-121">ReaderQuotas</span></span>  
 <span data-ttu-id="378b2-122">Type de données : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="378b2-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="378b2-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="378b2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="378b2-124">Quotas des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="378b2-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="378b2-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="378b2-125">Requirements</span></span>  
  
|<span data-ttu-id="378b2-126">MOF</span><span class="sxs-lookup"><span data-stu-id="378b2-126">MOF</span></span>|<span data-ttu-id="378b2-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="378b2-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="378b2-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="378b2-128">Namespace</span></span>|<span data-ttu-id="378b2-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="378b2-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="378b2-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="378b2-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
