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
ms.workload: dotnet
ms.openlocfilehash: 062b45eb5d627903142ca1a5fd4db6df0855384b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="de6d4-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="de6d4-102">TransportBindingElement</span></span>
<span data-ttu-id="de6d4-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="de6d4-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de6d4-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="de6d4-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="de6d4-105">Methods</span></span>  
 <span data-ttu-id="de6d4-106">La classe TransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="de6d4-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="de6d4-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="de6d4-107">Properties</span></span>  
 <span data-ttu-id="de6d4-108">La classe TransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="de6d4-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="de6d4-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="de6d4-109">ManualAddressing</span></span>  
 <span data-ttu-id="de6d4-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="de6d4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="de6d4-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="de6d4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6d4-112">Valeur booléenne qui spécifie si l'utilisateur souhaite prendre le contrôle de l'adressage des messages.</span><span class="sxs-lookup"><span data-stu-id="de6d4-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="de6d4-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="de6d4-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="de6d4-114">Type de données : sint64</span><span class="sxs-lookup"><span data-stu-id="de6d4-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="de6d4-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="de6d4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6d4-116">Taille maximale du pool de mémoires tampons pour la liaison.</span><span class="sxs-lookup"><span data-stu-id="de6d4-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="de6d4-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="de6d4-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="de6d4-118">Type de données : sint64</span><span class="sxs-lookup"><span data-stu-id="de6d4-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="de6d4-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="de6d4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6d4-120">Taille maximale d'un message traité par cette liaison.</span><span class="sxs-lookup"><span data-stu-id="de6d4-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="de6d4-121">Scheme</span><span class="sxs-lookup"><span data-stu-id="de6d4-121">Scheme</span></span>  
 <span data-ttu-id="de6d4-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="de6d4-122">Data type: string</span></span>  
  
 <span data-ttu-id="de6d4-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="de6d4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de6d4-124">Schéma d'URI pour le transport.</span><span class="sxs-lookup"><span data-stu-id="de6d4-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6d4-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="de6d4-125">Requirements</span></span>  
  
|<span data-ttu-id="de6d4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="de6d4-126">MOF</span></span>|<span data-ttu-id="de6d4-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="de6d4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="de6d4-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="de6d4-128">Namespace</span></span>|<span data-ttu-id="de6d4-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="de6d4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de6d4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de6d4-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
