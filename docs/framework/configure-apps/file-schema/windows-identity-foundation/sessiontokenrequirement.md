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
ms.workload: dotnet
ms.openlocfilehash: 5a141dd83cb7ef1271906871097eb68da174d22f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="b5a49-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="b5a49-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="b5a49-103">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="b5a49-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="b5a49-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b5a49-104">\<system.identityModel></span></span>  
<span data-ttu-id="b5a49-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b5a49-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b5a49-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b5a49-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b5a49-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b5a49-107">\<add></span></span>  
<span data-ttu-id="b5a49-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="b5a49-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a49-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5a49-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5a49-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b5a49-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b5a49-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b5a49-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5a49-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b5a49-112">Attributes</span></span>  
  
|<span data-ttu-id="b5a49-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5a49-113">Attribute</span></span>|<span data-ttu-id="b5a49-114">Description</span><span class="sxs-lookup"><span data-stu-id="b5a49-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5a49-115">durée de vie</span><span class="sxs-lookup"><span data-stu-id="b5a49-115">lifetime</span></span>|<span data-ttu-id="b5a49-116">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="b5a49-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5a49-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b5a49-117">Child Elements</span></span>  
 <span data-ttu-id="b5a49-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b5a49-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5a49-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b5a49-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b5a49-120">Élément</span><span class="sxs-lookup"><span data-stu-id="b5a49-120">Element</span></span>|<span data-ttu-id="b5a49-121">Description</span><span class="sxs-lookup"><span data-stu-id="b5a49-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5a49-122">\<add></span><span class="sxs-lookup"><span data-stu-id="b5a49-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b5a49-123">Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="b5a49-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b5a49-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5a49-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
