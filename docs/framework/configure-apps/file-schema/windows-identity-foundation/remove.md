---
title: '&lt;remove&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 15c2561487eecb44cf3542768de0a77d1dd6713d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt"></a><span data-ttu-id="1f696-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="1f696-102">&lt;remove&gt;</span></span>
<span data-ttu-id="1f696-103">Supprime le Gestionnaire de jetons de sécurité spécifié de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="1f696-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="1f696-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="1f696-104">\<system.identityModel></span></span>  
<span data-ttu-id="1f696-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1f696-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1f696-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1f696-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1f696-107">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="1f696-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f696-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f696-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f696-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1f696-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1f696-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1f696-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f696-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f696-111">Attributes</span></span>  
  
|<span data-ttu-id="1f696-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="1f696-112">Attribute</span></span>|<span data-ttu-id="1f696-113">Description</span><span class="sxs-lookup"><span data-stu-id="1f696-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f696-114">type</span><span class="sxs-lookup"><span data-stu-id="1f696-114">type</span></span>|<span data-ttu-id="1f696-115">Le nom de type CLR du Gestionnaire de jetons à supprimer.</span><span class="sxs-lookup"><span data-stu-id="1f696-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="1f696-116">Pour plus d’informations sur la façon de spécifier le `type` d’attribut, consultez [références de Type personnalisé](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="1f696-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="1f696-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1f696-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f696-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f696-118">Child Elements</span></span>  
 <span data-ttu-id="1f696-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1f696-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f696-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f696-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1f696-121">Élément</span><span class="sxs-lookup"><span data-stu-id="1f696-121">Element</span></span>|<span data-ttu-id="1f696-122">Description</span><span class="sxs-lookup"><span data-stu-id="1f696-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f696-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1f696-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="1f696-124">Spécifie une collection de gestionnaires de jetons de sécurité qui sont enregistrés avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1f696-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f696-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f696-125">Example</span></span>  
 <span data-ttu-id="1f696-126">Le code XML suivant illustre l’utilisation de la `<add>` et `<remove>` éléments pour remplacer le Gestionnaire de jetons de session par défaut avec un gestionnaire de jeton de session personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1f696-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="1f696-127">Le code XML provient de la `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="1f696-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
