---
title: "&lt;connectionManagement&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e3380ce1e8e798740214feee0e76d9949caa6bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="aa6de-102">&lt;connectionManagement&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="aa6de-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="aa6de-103">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="aa6de-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="aa6de-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa6de-104">\<configuration></span></span>  
<span data-ttu-id="aa6de-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="aa6de-105">\<system.net></span></span>  
<span data-ttu-id="aa6de-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="aa6de-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa6de-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa6de-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa6de-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aa6de-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa6de-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="aa6de-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa6de-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="aa6de-110">Attributes</span></span>  
 <span data-ttu-id="aa6de-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="aa6de-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aa6de-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aa6de-112">Child Elements</span></span>  
  
|<span data-ttu-id="aa6de-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="aa6de-113">**Element**</span></span>|<span data-ttu-id="aa6de-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="aa6de-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aa6de-115">add</span><span class="sxs-lookup"><span data-stu-id="aa6de-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="aa6de-116">Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="aa6de-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="aa6de-117">clear</span><span class="sxs-lookup"><span data-stu-id="aa6de-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="aa6de-118">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="aa6de-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="aa6de-119">remove</span><span class="sxs-lookup"><span data-stu-id="aa6de-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="aa6de-120">Supprime une adresse IP ou le nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="aa6de-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa6de-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aa6de-121">Parent Elements</span></span>  
  
|<span data-ttu-id="aa6de-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="aa6de-122">**Element**</span></span>|<span data-ttu-id="aa6de-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="aa6de-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aa6de-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="aa6de-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="aa6de-125">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="aa6de-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa6de-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa6de-126">Remarks</span></span>  
 <span data-ttu-id="aa6de-127">Le `connectionManagement` élément définit le nombre maximal de connexions à un serveur ou un groupe de serveurs.</span><span class="sxs-lookup"><span data-stu-id="aa6de-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="aa6de-128">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="aa6de-128">Configuration Files</span></span>  
 <span data-ttu-id="aa6de-129">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="aa6de-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa6de-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa6de-130">Example</span></span>  
 <span data-ttu-id="aa6de-131">L’exemple suivant configure une application d’utiliser quatre connexions au serveur www.contoso.com et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="aa6de-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa6de-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa6de-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="aa6de-133">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="aa6de-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
