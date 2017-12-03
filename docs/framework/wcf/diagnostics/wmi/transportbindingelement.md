---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2605e1a1f88434a9052059ac3ebdce429d6d6c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="2ea70-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2ea70-102">TransportBindingElement</span></span>
<span data-ttu-id="2ea70-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2ea70-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ea70-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2ea70-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2ea70-105">Methods</span></span>  
 <span data-ttu-id="2ea70-106">La classe TransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="2ea70-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2ea70-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2ea70-107">Properties</span></span>  
 <span data-ttu-id="2ea70-108">La classe TransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ea70-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="2ea70-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="2ea70-109">ManualAddressing</span></span>  
 <span data-ttu-id="2ea70-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="2ea70-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2ea70-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2ea70-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2ea70-112">Valeur booléenne qui spécifie si l'utilisateur souhaite prendre le contrôle de l'adressage des messages.</span><span class="sxs-lookup"><span data-stu-id="2ea70-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="2ea70-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2ea70-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="2ea70-114">Type de données : sint64</span><span class="sxs-lookup"><span data-stu-id="2ea70-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="2ea70-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2ea70-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2ea70-116">Taille maximale du pool de mémoires tampons pour la liaison.</span><span class="sxs-lookup"><span data-stu-id="2ea70-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="2ea70-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2ea70-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="2ea70-118">Type de données : sint64</span><span class="sxs-lookup"><span data-stu-id="2ea70-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="2ea70-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2ea70-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2ea70-120">Taille maximale d'un message traité par cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2ea70-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="2ea70-121">Scheme</span><span class="sxs-lookup"><span data-stu-id="2ea70-121">Scheme</span></span>  
 <span data-ttu-id="2ea70-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="2ea70-122">Data type: string</span></span>  
  
 <span data-ttu-id="2ea70-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2ea70-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2ea70-124">Schéma d'URI pour le transport.</span><span class="sxs-lookup"><span data-stu-id="2ea70-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea70-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2ea70-125">Requirements</span></span>  
  
|<span data-ttu-id="2ea70-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2ea70-126">MOF</span></span>|<span data-ttu-id="2ea70-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2ea70-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2ea70-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="2ea70-128">Namespace</span></span>|<span data-ttu-id="2ea70-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2ea70-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ea70-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea70-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
