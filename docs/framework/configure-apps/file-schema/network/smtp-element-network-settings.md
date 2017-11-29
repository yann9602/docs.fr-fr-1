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
ms.openlocfilehash: 17b4050c43354da7e7ba6c3ea13a0c7621faf0a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="a163f-102">&lt;SMTP&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a163f-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a163f-103">Configure le format de remise, de la méthode de remise et à partir de l’adresse pour l’envoi de messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="a163f-103">Configures the delivery format, delivery method, and from address for sending e-mails.</span></span>  
  
 <span data-ttu-id="a163f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a163f-104">\<configuration></span></span>  
<span data-ttu-id="a163f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="a163f-105">\<system.net></span></span>  
<span data-ttu-id="a163f-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="a163f-106">\<mailSettings></span></span>  
<span data-ttu-id="a163f-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="a163f-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a163f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a163f-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a163f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a163f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a163f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a163f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a163f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a163f-111">Attributes</span></span>  
  
|<span data-ttu-id="a163f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="a163f-112">Attribute</span></span>|<span data-ttu-id="a163f-113">Description</span><span class="sxs-lookup"><span data-stu-id="a163f-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="a163f-114">Spécifie le format de remise de messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="a163f-114">Specifies the delivery format for outgoing e-mails.</span></span> <span data-ttu-id="a163f-115">Les valeurs acceptables sont SevenBit et International.</span><span class="sxs-lookup"><span data-stu-id="a163f-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="a163f-116">Spécifie la méthode de remise pour les messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="a163f-116">Specifies the delivery method for e-mails.</span></span> <span data-ttu-id="a163f-117">Les valeurs acceptables sont network, pickupDirectoryFromIis et specifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="a163f-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="a163f-118">Spécifie l’adresse d’origine de messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="a163f-118">Specifies the from address for outgoing e-mails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a163f-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a163f-119">Child Elements</span></span>  
  
|<span data-ttu-id="a163f-120">Attribut</span><span class="sxs-lookup"><span data-stu-id="a163f-120">Attribute</span></span>|<span data-ttu-id="a163f-121">Description</span><span class="sxs-lookup"><span data-stu-id="a163f-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="a163f-122">Configure le répertoire local pour un serveur SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="a163f-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="a163f-123">Configure les options réseau pour un serveur SMTP externe.</span><span class="sxs-lookup"><span data-stu-id="a163f-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a163f-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a163f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a163f-125">**Élément**</span><span class="sxs-lookup"><span data-stu-id="a163f-125">**Element**</span></span>|<span data-ttu-id="a163f-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="a163f-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a163f-127">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a163f-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="a163f-128">Configure les options d’envoi du courrier.</span><span class="sxs-lookup"><span data-stu-id="a163f-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a163f-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="a163f-129">Example</span></span>  
 <span data-ttu-id="a163f-130">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques en utilisant les informations d’identification de réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="a163f-130">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a163f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a163f-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="a163f-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a163f-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
