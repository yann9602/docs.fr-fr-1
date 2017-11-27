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
ms.openlocfilehash: 177639b973bf8c597bc8b994d37c99647c72feb8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="940aa-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="940aa-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="940aa-103">Configure le certificat X.509 utilisé pour chiffrer et déchiffrer les jetons.</span><span class="sxs-lookup"><span data-stu-id="940aa-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="940aa-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="940aa-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="940aa-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="940aa-105">\<federationConfiguration></span></span>  
<span data-ttu-id="940aa-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="940aa-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="940aa-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="940aa-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="940aa-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="940aa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="940aa-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="940aa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="940aa-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="940aa-110">Attributes</span></span>  
 <span data-ttu-id="940aa-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="940aa-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="940aa-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="940aa-112">Child Elements</span></span>  
  
|<span data-ttu-id="940aa-113">Élément</span><span class="sxs-lookup"><span data-stu-id="940aa-113">Element</span></span>|<span data-ttu-id="940aa-114">Description</span><span class="sxs-lookup"><span data-stu-id="940aa-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="940aa-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="940aa-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="940aa-116">Spécifie les paramètres qui sont utilisés pour rechercher et valider un certificat X.509 dans un magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="940aa-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="940aa-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="940aa-117">Parent Elements</span></span>  
  
|<span data-ttu-id="940aa-118">Élément</span><span class="sxs-lookup"><span data-stu-id="940aa-118">Element</span></span>|<span data-ttu-id="940aa-119">Description</span><span class="sxs-lookup"><span data-stu-id="940aa-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="940aa-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="940aa-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="940aa-121">Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="940aa-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="940aa-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="940aa-122">Example</span></span>  
 <span data-ttu-id="940aa-123">Le code XML suivant illustre l’utilisation de la \<serviceCertificate > élément.</span><span class="sxs-lookup"><span data-stu-id="940aa-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="940aa-124">Le code XML provient de la `CustomToken` exemple.</span><span class="sxs-lookup"><span data-stu-id="940aa-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
