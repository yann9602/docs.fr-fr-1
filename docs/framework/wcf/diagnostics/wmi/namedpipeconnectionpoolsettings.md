---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18740c4c87aaeafcd0a28991376e0c45fe688223
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="6ac3e-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6ac3e-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="6ac3e-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6ac3e-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ac3e-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6ac3e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6ac3e-105">Methods</span></span>  
 <span data-ttu-id="6ac3e-106">La classe NamedPipeConnectionPoolSettings ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="6ac3e-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6ac3e-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6ac3e-107">Properties</span></span>  
 <span data-ttu-id="6ac3e-108">La classe NamedPipeConnectionPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ac3e-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="6ac3e-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="6ac3e-109">GroupName</span></span>  
 <span data-ttu-id="6ac3e-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="6ac3e-110">Data type: string</span></span>  
  
 <span data-ttu-id="6ac3e-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6ac3e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ac3e-112">Nom de groupe du pool de connexions utilisé par l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="6ac3e-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="6ac3e-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="6ac3e-113">IdleTimeout</span></span>  
 <span data-ttu-id="6ac3e-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="6ac3e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="6ac3e-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6ac3e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ac3e-116">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="6ac3e-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="6ac3e-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="6ac3e-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="6ac3e-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="6ac3e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="6ac3e-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6ac3e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ac3e-120">Nombre maximal de connexions sortantes pour chaque point de terminaison sur le client.</span><span class="sxs-lookup"><span data-stu-id="6ac3e-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac3e-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ac3e-121">Requirements</span></span>  
  
|<span data-ttu-id="6ac3e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6ac3e-122">MOF</span></span>|<span data-ttu-id="6ac3e-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6ac3e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6ac3e-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="6ac3e-124">Namespace</span></span>|<span data-ttu-id="6ac3e-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6ac3e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ac3e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ac3e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
