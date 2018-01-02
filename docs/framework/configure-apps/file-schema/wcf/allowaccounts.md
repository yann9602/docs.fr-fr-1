---
title: '&lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1716aa77808b2a9f8f3ca903dabf81b21b8f709
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="e16d6-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="e16d6-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="e16d6-103">Contient une collection d'éléments de configuration qui spécifient les comptes d'utilisateurs pour les processus qui hébergent des services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] et qui disposent d'un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="e16d6-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="e16d6-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="e16d6-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16d6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e16d6-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e16d6-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e16d6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e16d6-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e16d6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e16d6-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e16d6-108">Attributes</span></span>  
 <span data-ttu-id="e16d6-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e16d6-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e16d6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e16d6-110">Child Elements</span></span>  
  
|<span data-ttu-id="e16d6-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e16d6-111">Attribute</span></span>|<span data-ttu-id="e16d6-112">Description</span><span class="sxs-lookup"><span data-stu-id="e16d6-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e16d6-113">\<add></span><span class="sxs-lookup"><span data-stu-id="e16d6-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="e16d6-114">Ajoute un compte d'utilisateur pour les processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage</span><span class="sxs-lookup"><span data-stu-id="e16d6-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e16d6-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e16d6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e16d6-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e16d6-116">Element</span></span>|<span data-ttu-id="e16d6-117">Description</span><span class="sxs-lookup"><span data-stu-id="e16d6-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e16d6-118">[\<NET.PIPE >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) ou [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="e16d6-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="e16d6-119">Spécifie les paramètres de configuration pour le canal du réseau ou les services de partage TCP.</span><span class="sxs-lookup"><span data-stu-id="e16d6-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e16d6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e16d6-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
