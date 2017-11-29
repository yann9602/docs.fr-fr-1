---
title: "&lt;Supprimez&gt; , élément pour connectionManagement (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 92536ad7605211f3a7f606920b054a217427c8f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="24308-102">&lt;Supprimez&gt; , élément pour connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="24308-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="24308-103">Supprime une adresse IP ou le nom DNS de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="24308-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="24308-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="24308-104">\<configuration></span></span>  
<span data-ttu-id="24308-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="24308-105">\<system.net></span></span>  
<span data-ttu-id="24308-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="24308-106">\<connectionManagement></span></span>  
<span data-ttu-id="24308-107">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="24308-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24308-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24308-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24308-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="24308-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24308-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="24308-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24308-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="24308-111">Attributes</span></span>  
  
|<span data-ttu-id="24308-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="24308-112">**Attribute**</span></span>|<span data-ttu-id="24308-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="24308-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="24308-114">Une adresse IP ou le nom DNS.</span><span class="sxs-lookup"><span data-stu-id="24308-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24308-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="24308-115">Child Elements</span></span>  
 <span data-ttu-id="24308-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="24308-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24308-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="24308-117">Parent Elements</span></span>  
  
|<span data-ttu-id="24308-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="24308-118">**Element**</span></span>|<span data-ttu-id="24308-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="24308-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="24308-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="24308-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="24308-121">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="24308-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24308-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="24308-122">Remarks</span></span>  
 <span data-ttu-id="24308-123">Le `remove` élément supprime l’entrée de liste de gestion de connexion pour le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="24308-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="24308-124">La valeur de la `address` attribut doit être un nom d’hôte ou adresse IP valide.</span><span class="sxs-lookup"><span data-stu-id="24308-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="24308-125">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="24308-125">Configuration Files</span></span>  
 <span data-ttu-id="24308-126">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="24308-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24308-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="24308-127">Example</span></span>  
 <span data-ttu-id="24308-128">L’exemple suivant supprime toutes les entrées de liste de gestion de connexion pour le serveur www.adventure-works.com, puis configure une application d’utiliser quatre connexions au serveur www.contoso.com et deux connexions à tous les autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="24308-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24308-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24308-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="24308-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="24308-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
