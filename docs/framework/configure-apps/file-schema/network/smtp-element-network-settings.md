---
title: "&lt;SMTP&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 598fe3dc2a49187e923cd689f863d0a3327e735f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="60898-102">&lt;SMTP&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="60898-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="60898-103">Configure le format de remise, de la méthode de remise et à partir de l’adresse pour l’envoi de messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="60898-103">Configures the delivery format, delivery method, and from address for sending e-mails.</span></span>  
  
 <span data-ttu-id="60898-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="60898-104">\<configuration></span></span>  
<span data-ttu-id="60898-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="60898-105">\<system.net></span></span>  
<span data-ttu-id="60898-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="60898-106">\<mailSettings></span></span>  
<span data-ttu-id="60898-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="60898-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60898-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60898-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60898-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="60898-109">Attributes and Elements</span></span>  
 <span data-ttu-id="60898-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="60898-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60898-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="60898-111">Attributes</span></span>  
  
|<span data-ttu-id="60898-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="60898-112">Attribute</span></span>|<span data-ttu-id="60898-113">Description</span><span class="sxs-lookup"><span data-stu-id="60898-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="60898-114">Spécifie le format de remise de messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="60898-114">Specifies the delivery format for outgoing e-mails.</span></span> <span data-ttu-id="60898-115">Les valeurs acceptables sont SevenBit et International.</span><span class="sxs-lookup"><span data-stu-id="60898-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="60898-116">Spécifie la méthode de remise pour les messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="60898-116">Specifies the delivery method for e-mails.</span></span> <span data-ttu-id="60898-117">Les valeurs acceptables sont network, pickupDirectoryFromIis et specifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="60898-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="60898-118">Spécifie l’adresse d’origine de messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="60898-118">Specifies the from address for outgoing e-mails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60898-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="60898-119">Child Elements</span></span>  
  
|<span data-ttu-id="60898-120">Attribut</span><span class="sxs-lookup"><span data-stu-id="60898-120">Attribute</span></span>|<span data-ttu-id="60898-121">Description</span><span class="sxs-lookup"><span data-stu-id="60898-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="60898-122">Configure le répertoire local pour un serveur SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="60898-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="60898-123">Configure les options réseau pour un serveur SMTP externe.</span><span class="sxs-lookup"><span data-stu-id="60898-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60898-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="60898-124">Parent Elements</span></span>  
  
|<span data-ttu-id="60898-125">**Élément**</span><span class="sxs-lookup"><span data-stu-id="60898-125">**Element**</span></span>|<span data-ttu-id="60898-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="60898-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="60898-127">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="60898-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="60898-128">Configure les options d’envoi du courrier.</span><span class="sxs-lookup"><span data-stu-id="60898-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="60898-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="60898-129">Example</span></span>  
 <span data-ttu-id="60898-130">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques en utilisant les informations d’identification de réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="60898-130">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60898-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60898-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="60898-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="60898-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
