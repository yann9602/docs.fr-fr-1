---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74dd0827ee073d57c82729ec1e6a9a672aa1f404
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="e7051-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="e7051-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="e7051-103">Spécifie un type personnalisé pour la validation de certificat.</span><span class="sxs-lookup"><span data-stu-id="e7051-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="e7051-104">Ce type est utilisé uniquement si la `certificateValidationMode` attribut de la [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="e7051-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="e7051-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="e7051-105">\<system.identityModel></span></span>  
<span data-ttu-id="e7051-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e7051-106">\<identityConfiguration></span></span>  
<span data-ttu-id="e7051-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="e7051-107">\<certificateValidation></span></span>  
<span data-ttu-id="e7051-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="e7051-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7051-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7051-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7051-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7051-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e7051-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7051-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7051-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7051-112">Attributes</span></span>  
  
|<span data-ttu-id="e7051-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7051-113">Attribute</span></span>|<span data-ttu-id="e7051-114">Description</span><span class="sxs-lookup"><span data-stu-id="e7051-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7051-115">type</span><span class="sxs-lookup"><span data-stu-id="e7051-115">type</span></span>|<span data-ttu-id="e7051-116">Spécifie un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="e7051-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="e7051-117">Définir le `certificateValidationMode` attribut de la [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) élément à « Custom » pour utiliser ce type.</span><span class="sxs-lookup"><span data-stu-id="e7051-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="e7051-118">Pour plus d’informations sur la façon de spécifier le `type` d’attribut, consultez [références de Type personnalisé](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7051-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="e7051-119">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e7051-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7051-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7051-120">Child Elements</span></span>  
 <span data-ttu-id="e7051-121">None</span><span class="sxs-lookup"><span data-stu-id="e7051-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7051-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7051-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e7051-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e7051-123">Element</span></span>|<span data-ttu-id="e7051-124">Description</span><span class="sxs-lookup"><span data-stu-id="e7051-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7051-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="e7051-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="e7051-126">Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="e7051-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7051-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7051-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
