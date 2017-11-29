---
title: "&lt;publisherPolicy&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654887c870a7f620c52fa402d6324de39fdb2feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="f0e8f-102">&lt;publisherPolicy&gt; élément</span><span class="sxs-lookup"><span data-stu-id="f0e8f-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="f0e8f-103">Spécifie si le runtime applique la stratégie de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="f0e8f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f0e8f-104">\<configuration></span></span>  
<span data-ttu-id="f0e8f-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="f0e8f-105">\<runtime></span></span>  
<span data-ttu-id="f0e8f-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="f0e8f-106">\<assemblyBinding></span></span>  
<span data-ttu-id="f0e8f-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="f0e8f-107">\<dependentAssembly></span></span>  
<span data-ttu-id="f0e8f-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="f0e8f-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e8f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0e8f-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0e8f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f0e8f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0e8f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0e8f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f0e8f-112">Attributes</span></span>  
  
|<span data-ttu-id="f0e8f-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f0e8f-113">Attribute</span></span>|<span data-ttu-id="f0e8f-114">Description</span><span class="sxs-lookup"><span data-stu-id="f0e8f-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="f0e8f-115">Spécifie s’il faut appliquer la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="f0e8f-116">appliquer l’attribut</span><span class="sxs-lookup"><span data-stu-id="f0e8f-116">apply Attribute</span></span>  
  
|<span data-ttu-id="f0e8f-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="f0e8f-117">Value</span></span>|<span data-ttu-id="f0e8f-118">Description</span><span class="sxs-lookup"><span data-stu-id="f0e8f-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="f0e8f-119">Applique la stratégie de serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-119">Applies publisher policy.</span></span> <span data-ttu-id="f0e8f-120">Il s'agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="f0e8f-121">N’applique pas la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0e8f-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f0e8f-122">Child Elements</span></span>  
 <span data-ttu-id="f0e8f-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0e8f-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f0e8f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f0e8f-125">Élément</span><span class="sxs-lookup"><span data-stu-id="f0e8f-125">Element</span></span>|<span data-ttu-id="f0e8f-126">Description</span><span class="sxs-lookup"><span data-stu-id="f0e8f-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f0e8f-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f0e8f-128">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0e8f-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0e8f-129">Remarks</span></span>  
 <span data-ttu-id="f0e8f-130">Lorsqu’un fournisseur de composant publie une nouvelle version d’un assembly, le fournisseur peut inclure une stratégie d’éditeur pour les applications qui utilisent l’ancienne version désormais utilisent la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="f0e8f-131">Pour spécifier s’il faut appliquer la stratégie d’éditeur pour un assembly particulier, placez le  **\<publisherPolicy >** élément dans le  **\<dependentAssembly >** élément.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="f0e8f-132">Le paramètre par défaut pour le **appliquer** attribut est **Oui**.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="f0e8f-133">Définition de la **appliquer** attribut **aucun** remplacements précédents **Oui** paramètres d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="f0e8f-134">Autorisation est requise pour une application ignore explicitement la stratégie du serveur de publication à l’aide du [ \<publisherPolicy appliquer = « no » / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) élément dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="f0e8f-135">L’autorisation est accordée en définissant le <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur le <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="f0e8f-136">Pour plus d’informations, consultez [autorisation de sécurité pour la Redirection de liaison d’Assembly](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="f0e8f-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0e8f-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="f0e8f-137">Example</span></span>  
 <span data-ttu-id="f0e8f-138">L’exemple suivant désactive la stratégie de serveur de publication pour l’assembly, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="f0e8f-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0e8f-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0e8f-139">See Also</span></span>  
 [<span data-ttu-id="f0e8f-140">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="f0e8f-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f0e8f-141">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="f0e8f-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f0e8f-142">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="f0e8f-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="f0e8f-143">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="f0e8f-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
