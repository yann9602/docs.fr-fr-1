---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1e026296745f6fc40171866c81f91818789e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="5bdcc-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="5bdcc-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="5bdcc-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="5bdcc-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bdcc-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5bdcc-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5bdcc-105">Methods</span></span>  
 <span data-ttu-id="5bdcc-106">La classe TextMessageEncodingBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="5bdcc-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5bdcc-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5bdcc-107">Properties</span></span>  
 <span data-ttu-id="5bdcc-108">La classe TextMessageEncodingBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bdcc-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="5bdcc-109">Encodage</span><span class="sxs-lookup"><span data-stu-id="5bdcc-109">Encoding</span></span>  
 <span data-ttu-id="5bdcc-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5bdcc-110">Data type: string</span></span>  
  
 <span data-ttu-id="5bdcc-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5bdcc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bdcc-112">Encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="5bdcc-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="5bdcc-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="5bdcc-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="5bdcc-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="5bdcc-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="5bdcc-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5bdcc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bdcc-116">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="5bdcc-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="5bdcc-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="5bdcc-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="5bdcc-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="5bdcc-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="5bdcc-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5bdcc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bdcc-120">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="5bdcc-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="5bdcc-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="5bdcc-121">ReaderQuotas</span></span>  
 <span data-ttu-id="5bdcc-122">Type de données : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="5bdcc-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="5bdcc-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5bdcc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bdcc-124">Quotas des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="5bdcc-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bdcc-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5bdcc-125">Requirements</span></span>  
  
|<span data-ttu-id="5bdcc-126">MOF</span><span class="sxs-lookup"><span data-stu-id="5bdcc-126">MOF</span></span>|<span data-ttu-id="5bdcc-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5bdcc-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5bdcc-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5bdcc-128">Namespace</span></span>|<span data-ttu-id="5bdcc-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5bdcc-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bdcc-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bdcc-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
