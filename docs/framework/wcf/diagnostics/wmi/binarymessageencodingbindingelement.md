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
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="11d21-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="11d21-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="11d21-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="11d21-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d21-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="11d21-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="11d21-105">Methods</span></span>  
 <span data-ttu-id="11d21-106">La classe BinaryMessageEncodingBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="11d21-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="11d21-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="11d21-107">Properties</span></span>  
 <span data-ttu-id="11d21-108">La classe BinaryMessageEncodingBindingElement a les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="11d21-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="11d21-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="11d21-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="11d21-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="11d21-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="11d21-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="11d21-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d21-112">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="11d21-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="11d21-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="11d21-113">MaxSessionSize</span></span>  
 <span data-ttu-id="11d21-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="11d21-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="11d21-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="11d21-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d21-116">Valeur qui spécifie la taille, en octets, de la mémoire tampon utilisée pour l'encodage.</span><span class="sxs-lookup"><span data-stu-id="11d21-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="11d21-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="11d21-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="11d21-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="11d21-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="11d21-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="11d21-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d21-120">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="11d21-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="11d21-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="11d21-121">ReaderQuotas</span></span>  
 <span data-ttu-id="11d21-122">Type de données : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="11d21-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="11d21-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="11d21-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11d21-124">Quotas des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="11d21-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d21-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="11d21-125">Requirements</span></span>  
  
|<span data-ttu-id="11d21-126">MOF</span><span class="sxs-lookup"><span data-stu-id="11d21-126">MOF</span></span>|<span data-ttu-id="11d21-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="11d21-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="11d21-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="11d21-128">Namespace</span></span>|<span data-ttu-id="11d21-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="11d21-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11d21-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11d21-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
