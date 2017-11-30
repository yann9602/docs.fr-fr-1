---
title: "&lt;Désactivez&gt; , élément pour connectionManagement (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0fe32b20b9b0a0217ecef36f65ae1ee4084e92ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d1f2f-102">&lt;Désactivez&gt; , élément pour connectionManagement (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="d1f2f-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="d1f2f-103">Efface la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="d1f2f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d1f2f-104">\<configuration></span></span>  
<span data-ttu-id="d1f2f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="d1f2f-105">\<system.net></span></span>  
<span data-ttu-id="d1f2f-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="d1f2f-106">\<connectionManagement></span></span>  
<span data-ttu-id="d1f2f-107">\<Désactivez ></span><span class="sxs-lookup"><span data-stu-id="d1f2f-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f2f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1f2f-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1f2f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1f2f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1f2f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1f2f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1f2f-111">Attributes</span></span>  
 <span data-ttu-id="d1f2f-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="d1f2f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1f2f-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1f2f-113">Child Elements</span></span>  
 <span data-ttu-id="d1f2f-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1f2f-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1f2f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d1f2f-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="d1f2f-116">**Element**</span></span>|<span data-ttu-id="d1f2f-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="d1f2f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1f2f-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d1f2f-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="d1f2f-119">Spécifie le nombre maximal de connexions à un hôte réseau.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1f2f-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="d1f2f-120">Remarks</span></span>  
 <span data-ttu-id="d1f2f-121">Le `clear` élément efface toutes les entrées de la liste de gestion des connexions.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d1f2f-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d1f2f-122">Configuration Files</span></span>  
 <span data-ttu-id="d1f2f-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d1f2f-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1f2f-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1f2f-124">Example</span></span>  
 <span data-ttu-id="d1f2f-125">L’exemple suivant efface la liste de gestion des connexions et ajoute alors les nouvelles entrées de gestion de connexion pour le serveur www.contoso.com et tous les autres hôtes de réseau.</span><span class="sxs-lookup"><span data-stu-id="d1f2f-125">The following example clears the connection management list and then adds new connection management entries for the server www.contoso.com and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1f2f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1f2f-126">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="d1f2f-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="d1f2f-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
