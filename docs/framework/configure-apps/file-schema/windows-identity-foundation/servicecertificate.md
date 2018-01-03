---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1373d1e95a0e569f5e5cf433d305d008b4daf838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="4ab1f-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="4ab1f-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="4ab1f-103">Configure le certificat X.509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="4ab1f-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="4ab1f-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="4ab1f-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="4ab1f-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4ab1f-105">\<federationConfiguration></span></span>  
<span data-ttu-id="4ab1f-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="4ab1f-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab1f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ab1f-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ab1f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4ab1f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4ab1f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4ab1f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ab1f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4ab1f-110">Attributes</span></span>  
 <span data-ttu-id="4ab1f-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4ab1f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ab1f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4ab1f-112">Child Elements</span></span>  
  
|<span data-ttu-id="4ab1f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4ab1f-113">Element</span></span>|<span data-ttu-id="4ab1f-114">Description</span><span class="sxs-lookup"><span data-stu-id="4ab1f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ab1f-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="4ab1f-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="4ab1f-116">Spécifie les paramètres qui sont utilisés pour rechercher et valider un certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="4ab1f-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ab1f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4ab1f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4ab1f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="4ab1f-118">Element</span></span>|<span data-ttu-id="4ab1f-119">Description</span><span class="sxs-lookup"><span data-stu-id="4ab1f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ab1f-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="4ab1f-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="4ab1f-121">Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="4ab1f-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4ab1f-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ab1f-122">Example</span></span>  
 <span data-ttu-id="4ab1f-123">Le code XML suivant illustre l’utilisation de la \<serviceCertificate > élément.</span><span class="sxs-lookup"><span data-stu-id="4ab1f-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="4ab1f-124">Le code XML provient de la `CustomToken` exemple.</span><span class="sxs-lookup"><span data-stu-id="4ab1f-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
