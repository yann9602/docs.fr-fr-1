---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="d1bfb-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d1bfb-102">PeerSecuritySettings</span></span>
<span data-ttu-id="d1bfb-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d1bfb-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1bfb-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d1bfb-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d1bfb-105">Methods</span></span>  
 <span data-ttu-id="d1bfb-106">La classe PeerSecuritySettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d1bfb-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d1bfb-107">Properties</span></span>  
 <span data-ttu-id="d1bfb-108">La classe PeerSecuritySettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="d1bfb-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="d1bfb-109">Mode</span><span class="sxs-lookup"><span data-stu-id="d1bfb-109">Mode</span></span>  
 <span data-ttu-id="d1bfb-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="d1bfb-110">Data type: string</span></span>  
  
 <span data-ttu-id="d1bfb-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="d1bfb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1bfb-112">Utilisation ou non d’une sécurité au niveau du message et au niveau du transport par un point de terminaison configuré avec la liaison.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="d1bfb-113">Transport</span><span class="sxs-lookup"><span data-stu-id="d1bfb-113">Transport</span></span>  
 <span data-ttu-id="d1bfb-114">Type de données : PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d1bfb-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="d1bfb-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="d1bfb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1bfb-116">Paramètres de sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1bfb-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d1bfb-117">Requirements</span></span>  
  
|<span data-ttu-id="d1bfb-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d1bfb-118">MOF</span></span>|<span data-ttu-id="d1bfb-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d1bfb-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d1bfb-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="d1bfb-120">Namespace</span></span>|<span data-ttu-id="d1bfb-121">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d1bfb-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1bfb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1bfb-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
