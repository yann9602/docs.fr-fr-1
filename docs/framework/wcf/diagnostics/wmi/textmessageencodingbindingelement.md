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
ms.openlocfilehash: 966f1ae06f5d7e0dacb8b7d450463c75f783ef1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="32c66-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="32c66-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="32c66-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="32c66-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32c66-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="32c66-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="32c66-105">Methods</span></span>  
 <span data-ttu-id="32c66-106">La classe TextMessageEncodingBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="32c66-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="32c66-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="32c66-107">Properties</span></span>  
 <span data-ttu-id="32c66-108">La classe TextMessageEncodingBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="32c66-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="32c66-109">Encodage</span><span class="sxs-lookup"><span data-stu-id="32c66-109">Encoding</span></span>  
 <span data-ttu-id="32c66-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="32c66-110">Data type: string</span></span>  
  
 <span data-ttu-id="32c66-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="32c66-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32c66-112">Encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="32c66-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="32c66-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="32c66-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="32c66-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="32c66-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="32c66-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="32c66-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32c66-116">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="32c66-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="32c66-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="32c66-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="32c66-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="32c66-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="32c66-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="32c66-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32c66-120">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="32c66-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="32c66-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="32c66-121">ReaderQuotas</span></span>  
 <span data-ttu-id="32c66-122">Type de données : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="32c66-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="32c66-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="32c66-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32c66-124">Quotas des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="32c66-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32c66-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="32c66-125">Requirements</span></span>  
  
|<span data-ttu-id="32c66-126">MOF</span><span class="sxs-lookup"><span data-stu-id="32c66-126">MOF</span></span>|<span data-ttu-id="32c66-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="32c66-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="32c66-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="32c66-128">Namespace</span></span>|<span data-ttu-id="32c66-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32c66-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32c66-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32c66-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
