---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaec1b7d179810faaba016cfa0c5eb7e6c950ab6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="6de60-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6de60-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="6de60-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6de60-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de60-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6de60-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6de60-105">Methods</span></span>  
 <span data-ttu-id="6de60-106">La classe TcpConnectionPoolSettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="6de60-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6de60-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6de60-107">Properties</span></span>  
 <span data-ttu-id="6de60-108">La classe TcpConnectionPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="6de60-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="6de60-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="6de60-109">GroupName</span></span>  
 <span data-ttu-id="6de60-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="6de60-110">Data type: string</span></span>  
  
 <span data-ttu-id="6de60-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6de60-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6de60-112">Nom de groupe du pool de connexions utilisé par l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="6de60-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="6de60-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="6de60-113">IdleTimeout</span></span>  
 <span data-ttu-id="6de60-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="6de60-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="6de60-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6de60-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6de60-116">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="6de60-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="6de60-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="6de60-117">LeaseTimeout</span></span>  
 <span data-ttu-id="6de60-118">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="6de60-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="6de60-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6de60-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6de60-120">Période maximale d'exécution de l'opération de bail avant expiration du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="6de60-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="6de60-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="6de60-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="6de60-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="6de60-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="6de60-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6de60-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6de60-124">Nombre maximal de connexions sortantes pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6de60-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de60-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6de60-125">Requirements</span></span>  
  
|<span data-ttu-id="6de60-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6de60-126">MOF</span></span>|<span data-ttu-id="6de60-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6de60-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6de60-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="6de60-128">Namespace</span></span>|<span data-ttu-id="6de60-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6de60-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6de60-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de60-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
