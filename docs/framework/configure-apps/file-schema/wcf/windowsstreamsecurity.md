---
title: '&lt;windowsStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="11b1d-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="11b1d-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="11b1d-103">Spécifiez les paramètres de sécurité de flux de données Windows pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="11b1d-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="11b1d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="11b1d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="11b1d-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="11b1d-105">\<bindings></span></span>  
<span data-ttu-id="11b1d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="11b1d-106">\<customBinding></span></span>  
<span data-ttu-id="11b1d-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="11b1d-107">\<binding></span></span>  
<span data-ttu-id="11b1d-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="11b1d-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b1d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b1d-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b1d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="11b1d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11b1d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="11b1d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b1d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="11b1d-112">Attributes</span></span>  
  
|<span data-ttu-id="11b1d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="11b1d-113">Attribute</span></span>|<span data-ttu-id="11b1d-114">Description</span><span class="sxs-lookup"><span data-stu-id="11b1d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11b1d-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="11b1d-115">protectionLevel</span></span>|<span data-ttu-id="11b1d-116">Définit la sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="11b1d-116">Defines message-level security.</span></span> <span data-ttu-id="11b1d-117">La signature des messages atténue le risque de modification par un tiers pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="11b1d-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="11b1d-118">Le chiffrement garantit la confidentialité des données pendant le transport.</span><span class="sxs-lookup"><span data-stu-id="11b1d-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="11b1d-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="11b1d-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="11b1d-120">-None : Aucune protection.</span><span class="sxs-lookup"><span data-stu-id="11b1d-120">-   None: No protection.</span></span><br /><span data-ttu-id="11b1d-121">-Sign : Les Messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="11b1d-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="11b1d-122">-EncryptAndSign : Les Messages sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="11b1d-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="11b1d-123">La valeur par défaut est EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="11b1d-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="11b1d-124">Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="11b1d-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b1d-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="11b1d-125">Child Elements</span></span>  
 <span data-ttu-id="11b1d-126">None</span><span class="sxs-lookup"><span data-stu-id="11b1d-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11b1d-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="11b1d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="11b1d-128">Élément</span><span class="sxs-lookup"><span data-stu-id="11b1d-128">Element</span></span>|<span data-ttu-id="11b1d-129">Description</span><span class="sxs-lookup"><span data-stu-id="11b1d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11b1d-130">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="11b1d-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="11b1d-131">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="11b1d-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b1d-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="11b1d-132">Remarks</span></span>  
 <span data-ttu-id="11b1d-133">Les transports qui utilisent un protocole orienté flux de données, tel que TCP, et des canaux nommés prennent en charge les mises à niveau de transport basées sur le flux de données.</span><span class="sxs-lookup"><span data-stu-id="11b1d-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="11b1d-134">Plus spécifiquement, WCF fournit les mises à niveau de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="11b1d-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="11b1d-135">La configuration de cette sécurité des transports est encapsulée par cet élément de configuration, ainsi que par [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), qui peuvent être configuré et ajouté à une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="11b1d-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b1d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11b1d-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="11b1d-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="11b1d-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="11b1d-138">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="11b1d-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="11b1d-139">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="11b1d-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="11b1d-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="11b1d-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
