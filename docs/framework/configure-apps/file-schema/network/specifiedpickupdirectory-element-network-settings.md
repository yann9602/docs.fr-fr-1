---
title: "&lt;specifiedPickupDirectory&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e68ce8cac4048ee2df89d0241cc50242e20391a2
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="b39f4-102">&lt;specifiedPickupDirectory&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b39f4-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b39f4-103">Configure le répertoire local pour un serveur SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="b39f4-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="b39f4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b39f4-104">\<configuration></span></span>  
<span data-ttu-id="b39f4-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b39f4-105">\<system.net></span></span>  
<span data-ttu-id="b39f4-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="b39f4-106">\<mailSettings></span></span>  
<span data-ttu-id="b39f4-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="b39f4-107">\<smtp></span></span>  
<span data-ttu-id="b39f4-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="b39f4-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b39f4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b39f4-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b39f4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b39f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b39f4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b39f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b39f4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b39f4-112">Attributes</span></span>  
  
|<span data-ttu-id="b39f4-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b39f4-113">Attribute</span></span>|<span data-ttu-id="b39f4-114">Description</span><span class="sxs-lookup"><span data-stu-id="b39f4-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="b39f4-115">Le répertoire dans lequel enregistrent les applications de courrier électronique pour un traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="b39f4-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b39f4-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b39f4-116">Child Elements</span></span>  
 <span data-ttu-id="b39f4-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b39f4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b39f4-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b39f4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b39f4-119">Élément</span><span class="sxs-lookup"><span data-stu-id="b39f4-119">Element</span></span>|<span data-ttu-id="b39f4-120">Description</span><span class="sxs-lookup"><span data-stu-id="b39f4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b39f4-121">\<SMTP >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="b39f4-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="b39f4-122">Configure les options d’envoi du courrier SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="b39f4-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b39f4-123">Notes</span><span class="sxs-lookup"><span data-stu-id="b39f4-123">Remarks</span></span>  
 <span data-ttu-id="b39f4-124">Le `specifiedPickupDirectory` attribut définit le répertoire dans lequel les applications enregistrent les messages électroniques à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="b39f4-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b39f4-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="b39f4-125">Example</span></span>  
 <span data-ttu-id="b39f4-126">L’exemple suivant indique c:\maildrop comme répertoire de collecte de messagerie.</span><span class="sxs-lookup"><span data-stu-id="b39f4-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b39f4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b39f4-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="b39f4-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b39f4-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
