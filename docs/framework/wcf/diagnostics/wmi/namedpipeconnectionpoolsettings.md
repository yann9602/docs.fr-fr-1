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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf9c39334289cb30d1a01917c0be37da02fcdc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="b012c-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b012c-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="b012c-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b012c-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b012c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b012c-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b012c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b012c-105">Methods</span></span>  
 <span data-ttu-id="b012c-106">La classe NamedPipeConnectionPoolSettings ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="b012c-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b012c-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b012c-107">Properties</span></span>  
 <span data-ttu-id="b012c-108">La classe NamedPipeConnectionPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="b012c-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="b012c-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="b012c-109">GroupName</span></span>  
 <span data-ttu-id="b012c-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="b012c-110">Data type: string</span></span>  
  
 <span data-ttu-id="b012c-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="b012c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b012c-112">Nom de groupe du pool de connexions utilisé par l'élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="b012c-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="b012c-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="b012c-113">IdleTimeout</span></span>  
 <span data-ttu-id="b012c-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="b012c-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="b012c-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="b012c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b012c-116">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="b012c-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="b012c-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="b012c-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="b012c-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="b012c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b012c-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="b012c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b012c-120">Nombre maximal de connexions sortantes pour chaque point de terminaison sur le client.</span><span class="sxs-lookup"><span data-stu-id="b012c-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b012c-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b012c-121">Requirements</span></span>  
  
|<span data-ttu-id="b012c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b012c-122">MOF</span></span>|<span data-ttu-id="b012c-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b012c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b012c-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="b012c-124">Namespace</span></span>|<span data-ttu-id="b012c-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b012c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b012c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b012c-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
