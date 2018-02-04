---
title: "&lt;SMTP&gt; élément (paramètres réseau)"
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
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f5b2a3b7eec17fbdd12181c29f610d2b2ad32bd4
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="a7f7e-102">&lt;SMTP&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a7f7e-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a7f7e-103">Configure le format de remise, de la méthode de remise et à partir de l’adresse pour l’envoi des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="a7f7e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a7f7e-104">\<configuration></span></span>  
<span data-ttu-id="a7f7e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a7f7e-105">\<system.net></span></span>  
<span data-ttu-id="a7f7e-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="a7f7e-106">\<mailSettings></span></span>  
<span data-ttu-id="a7f7e-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="a7f7e-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f7e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f7e-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f7e-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7f7e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f7e-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f7e-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7f7e-111">Attributes</span></span>  
  
|<span data-ttu-id="a7f7e-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7f7e-112">Attribute</span></span>|<span data-ttu-id="a7f7e-113">Description</span><span class="sxs-lookup"><span data-stu-id="a7f7e-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="a7f7e-114">Spécifie le format de remise de messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="a7f7e-115">Les valeurs acceptables sont SevenBit et International.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="a7f7e-116">Spécifie la méthode de remise pour les messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="a7f7e-117">Les valeurs acceptables sont network, pickupDirectoryFromIis et SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="a7f7e-118">Spécifie l’adresse d’origine de messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f7e-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7f7e-119">Child Elements</span></span>  
  
|<span data-ttu-id="a7f7e-120">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7f7e-120">Attribute</span></span>|<span data-ttu-id="a7f7e-121">Description</span><span class="sxs-lookup"><span data-stu-id="a7f7e-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="a7f7e-122">Configure le répertoire local pour un serveur SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="a7f7e-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="a7f7e-123">Configure les options réseau pour un serveur SMTP externe.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f7e-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7f7e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f7e-125">**Élément**</span><span class="sxs-lookup"><span data-stu-id="a7f7e-125">**Element**</span></span>|<span data-ttu-id="a7f7e-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="a7f7e-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a7f7e-127">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a7f7e-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="a7f7e-128">Configure les options d’envoi du courrier.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a7f7e-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7f7e-129">Example</span></span>  
 <span data-ttu-id="a7f7e-130">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer un courrier électronique à l’aide des informations d’identification de réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="a7f7e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f7e-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="a7f7e-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a7f7e-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
