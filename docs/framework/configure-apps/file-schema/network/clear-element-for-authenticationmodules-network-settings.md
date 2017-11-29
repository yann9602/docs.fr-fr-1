---
title: "&lt;Désactivez&gt; , élément pour authenticationModules (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f056894148177e6b540fd45569140a996b6b888f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="898b0-102">&lt;Désactivez&gt; , élément pour authenticationModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="898b0-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="898b0-103">Efface tous les modules d’authentification de l’application.</span><span class="sxs-lookup"><span data-stu-id="898b0-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="898b0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="898b0-104">\<configuration></span></span>  
<span data-ttu-id="898b0-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="898b0-105">\<system.net></span></span>  
<span data-ttu-id="898b0-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="898b0-106">\<authenticationModules></span></span>  
<span data-ttu-id="898b0-107">\<Désactivez ></span><span class="sxs-lookup"><span data-stu-id="898b0-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898b0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="898b0-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="898b0-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="898b0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="898b0-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="898b0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="898b0-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="898b0-111">Attributes</span></span>  
 <span data-ttu-id="898b0-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="898b0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="898b0-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="898b0-113">Child Elements</span></span>  
 <span data-ttu-id="898b0-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="898b0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="898b0-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="898b0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="898b0-116">**Élément**</span><span class="sxs-lookup"><span data-stu-id="898b0-116">**Element**</span></span>|<span data-ttu-id="898b0-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="898b0-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="898b0-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="898b0-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="898b0-119">Spécifie les modules utilisés pour authentifier les demandes du réseau.</span><span class="sxs-lookup"><span data-stu-id="898b0-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="898b0-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="898b0-120">Remarks</span></span>  
 <span data-ttu-id="898b0-121">Le `clear` élément supprime tous les modules d’authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="898b0-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="898b0-122">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="898b0-122">Configuration Files</span></span>  
 <span data-ttu-id="898b0-123">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="898b0-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="898b0-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="898b0-124">Example</span></span>  
 <span data-ttu-id="898b0-125">L’exemple suivant supprime tous les modules d’authentification configuré.</span><span class="sxs-lookup"><span data-stu-id="898b0-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="898b0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="898b0-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="898b0-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="898b0-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
