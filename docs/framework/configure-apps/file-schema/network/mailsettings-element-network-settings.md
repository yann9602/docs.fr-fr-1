---
title: "&lt;mailSettings&gt; élément (paramètres réseau)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: ce7ec8bea57436ebd184cf0d593870999405f72f
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="97acf-102">&lt;mailSettings&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="97acf-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="97acf-103">Configure les options d’envoi du courrier.</span><span class="sxs-lookup"><span data-stu-id="97acf-103">Configures mail sending options.</span></span>  

<span data-ttu-id="97acf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="97acf-104">\<configuration></span></span>  
<span data-ttu-id="97acf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="97acf-105">\<system.net></span></span>  
<span data-ttu-id="97acf-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="97acf-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97acf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97acf-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97acf-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="97acf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="97acf-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="97acf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97acf-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="97acf-110">Attributes</span></span>  
 <span data-ttu-id="97acf-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="97acf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97acf-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="97acf-112">Child Elements</span></span>  
  
|<span data-ttu-id="97acf-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="97acf-113">Attribute</span></span>|<span data-ttu-id="97acf-114">Description</span><span class="sxs-lookup"><span data-stu-id="97acf-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="97acf-115">\<SMTP >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="97acf-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="97acf-116">Configure les options de Simple Mail Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="97acf-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97acf-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="97acf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="97acf-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="97acf-118">**Element**</span></span>|<span data-ttu-id="97acf-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="97acf-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="97acf-120">\<system.Net>, élément (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="97acf-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="97acf-121">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="97acf-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97acf-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="97acf-122">Example</span></span>  
 <span data-ttu-id="97acf-123">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer un courrier électronique à l’aide des informations d’identification de réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="97acf-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97acf-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97acf-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="97acf-125">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="97acf-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
