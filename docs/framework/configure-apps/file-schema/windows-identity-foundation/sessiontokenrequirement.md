---
title: '&lt;sessionTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b729f588d2195992b231661f7bb718240141fdd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="8d683-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="8d683-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="8d683-103">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="8d683-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="8d683-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="8d683-104">\<system.identityModel></span></span>  
<span data-ttu-id="8d683-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8d683-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8d683-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="8d683-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8d683-107">\<add></span><span class="sxs-lookup"><span data-stu-id="8d683-107">\<add></span></span>  
<span data-ttu-id="8d683-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="8d683-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d683-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d683-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d683-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d683-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d683-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d683-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d683-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d683-112">Attributes</span></span>  
  
|<span data-ttu-id="8d683-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="8d683-113">Attribute</span></span>|<span data-ttu-id="8d683-114">Description</span><span class="sxs-lookup"><span data-stu-id="8d683-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d683-115">durée de vie</span><span class="sxs-lookup"><span data-stu-id="8d683-115">lifetime</span></span>|<span data-ttu-id="8d683-116">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="8d683-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d683-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d683-117">Child Elements</span></span>  
 <span data-ttu-id="8d683-118">None</span><span class="sxs-lookup"><span data-stu-id="8d683-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d683-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d683-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d683-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8d683-120">Element</span></span>|<span data-ttu-id="8d683-121">Description</span><span class="sxs-lookup"><span data-stu-id="8d683-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d683-122">\<add></span><span class="sxs-lookup"><span data-stu-id="8d683-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="8d683-123">Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="8d683-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d683-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d683-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
