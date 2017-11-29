---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c2c5d54050216c91a318a407341c4ffb9cb687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="4a263-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4a263-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="4a263-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4a263-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a263-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a263-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4a263-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4a263-105">Methods</span></span>  
 <span data-ttu-id="4a263-106">La classe MsmqTransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="4a263-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a263-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4a263-107">Properties</span></span>  
 <span data-ttu-id="4a263-108">La classe MsmqTransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a263-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="4a263-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="4a263-109">MaxPoolSize</span></span>  
 <span data-ttu-id="4a263-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="4a263-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a263-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4a263-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a263-112">Taille maximale du pool contenant des objets de message MSMQ internes.</span><span class="sxs-lookup"><span data-stu-id="4a263-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="4a263-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="4a263-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="4a263-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="4a263-114">Data type: string</span></span>  
  
 <span data-ttu-id="4a263-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4a263-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a263-116">Valeur d'énumération qui indique le transport de canal de communication mis en file d'attente que cette liaison utilise.</span><span class="sxs-lookup"><span data-stu-id="4a263-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="4a263-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="4a263-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="4a263-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="4a263-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="4a263-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4a263-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a263-120">Retourne une valeur Boolean qui indique si les adresses de file d'attente doivent être converties à l'aide d'Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4a263-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a263-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4a263-121">Requirements</span></span>  
  
|<span data-ttu-id="4a263-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4a263-122">MOF</span></span>|<span data-ttu-id="4a263-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4a263-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4a263-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="4a263-124">Namespace</span></span>|<span data-ttu-id="4a263-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4a263-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a263-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a263-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
