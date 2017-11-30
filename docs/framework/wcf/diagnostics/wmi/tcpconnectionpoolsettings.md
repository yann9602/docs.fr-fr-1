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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="2aa1f-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2aa1f-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="2aa1f-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2aa1f-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2aa1f-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2aa1f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2aa1f-105">Methods</span></span>  
 <span data-ttu-id="2aa1f-106">La classe TcpConnectionPoolSettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="2aa1f-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2aa1f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2aa1f-107">Properties</span></span>  
 <span data-ttu-id="2aa1f-108">La classe TcpConnectionPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aa1f-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="2aa1f-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="2aa1f-109">GroupName</span></span>  
 <span data-ttu-id="2aa1f-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="2aa1f-110">Data type: string</span></span>  
  
 <span data-ttu-id="2aa1f-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2aa1f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2aa1f-112">Nom de groupe du pool de connexions utilisé par l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="2aa1f-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="2aa1f-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="2aa1f-113">IdleTimeout</span></span>  
 <span data-ttu-id="2aa1f-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="2aa1f-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="2aa1f-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2aa1f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2aa1f-116">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="2aa1f-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="2aa1f-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="2aa1f-117">LeaseTimeout</span></span>  
 <span data-ttu-id="2aa1f-118">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="2aa1f-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="2aa1f-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2aa1f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2aa1f-120">Période maximale d'exécution de l'opération de bail avant expiration du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="2aa1f-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="2aa1f-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="2aa1f-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="2aa1f-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="2aa1f-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="2aa1f-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2aa1f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2aa1f-124">Nombre maximal de connexions sortantes pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2aa1f-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aa1f-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2aa1f-125">Requirements</span></span>  
  
|<span data-ttu-id="2aa1f-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2aa1f-126">MOF</span></span>|<span data-ttu-id="2aa1f-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2aa1f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2aa1f-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="2aa1f-128">Namespace</span></span>|<span data-ttu-id="2aa1f-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2aa1f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2aa1f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2aa1f-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
