---
title: "&lt;mailSettings&gt; élément (paramètres réseau)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a42b10574a1f44d310f86fe3fa99490f2f1981c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="add9a-102">&lt;mailSettings&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="add9a-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="add9a-103">Configure les options d’envoi du courrier.</span><span class="sxs-lookup"><span data-stu-id="add9a-103">Configures mail sending options.</span></span>  

<span data-ttu-id="add9a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="add9a-104">\<configuration></span></span>  
<span data-ttu-id="add9a-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="add9a-105">\<system.net></span></span>  
<span data-ttu-id="add9a-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="add9a-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add9a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="add9a-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="add9a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="add9a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="add9a-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="add9a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="add9a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="add9a-110">Attributes</span></span>  
 <span data-ttu-id="add9a-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="add9a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="add9a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="add9a-112">Child Elements</span></span>  
  
|<span data-ttu-id="add9a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="add9a-113">Attribute</span></span>|<span data-ttu-id="add9a-114">Description</span><span class="sxs-lookup"><span data-stu-id="add9a-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="add9a-115">\<SMTP >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="add9a-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="add9a-116">Configure les options de Simple Mail Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="add9a-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="add9a-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="add9a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="add9a-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="add9a-118">**Element**</span></span>|<span data-ttu-id="add9a-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="add9a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="add9a-120">\<system.Net>, élément (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="add9a-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="add9a-121">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="add9a-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="add9a-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="add9a-122">Example</span></span>  
 <span data-ttu-id="add9a-123">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques en utilisant les informations d’identification de réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="add9a-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="add9a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="add9a-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="add9a-125">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="add9a-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
