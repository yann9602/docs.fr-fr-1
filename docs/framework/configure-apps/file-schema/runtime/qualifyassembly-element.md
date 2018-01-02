---
title: "&lt;qualifyAssembly&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7da2e1ac5c16f6e481c974794efceb12f102b1a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltqualifyassemblygt-element"></a><span data-ttu-id="9951f-102">&lt;qualifyAssembly&gt; élément</span><span class="sxs-lookup"><span data-stu-id="9951f-102">&lt;qualifyAssembly&gt; Element</span></span>
<span data-ttu-id="9951f-103">Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9951f-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="9951f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9951f-104">\<configuration></span></span>  
<span data-ttu-id="9951f-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="9951f-105">\<runtime></span></span>  
<span data-ttu-id="9951f-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="9951f-106">\<assemblyBinding></span></span>  
<span data-ttu-id="9951f-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="9951f-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9951f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9951f-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9951f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9951f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9951f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9951f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9951f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="9951f-111">Attributes</span></span>  
  
|<span data-ttu-id="9951f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="9951f-112">Attribute</span></span>|<span data-ttu-id="9951f-113">Description</span><span class="sxs-lookup"><span data-stu-id="9951f-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="9951f-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9951f-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9951f-115">Spécifie le nom partiel de l’assembly tel qu’il apparaît dans le code.</span><span class="sxs-lookup"><span data-stu-id="9951f-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="9951f-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9951f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="9951f-117">Spécifie le nom complet de l’assembly tel qu’il apparaît dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="9951f-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9951f-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9951f-118">Child Elements</span></span>  
 <span data-ttu-id="9951f-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9951f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9951f-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9951f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9951f-121">Élément</span><span class="sxs-lookup"><span data-stu-id="9951f-121">Element</span></span>|<span data-ttu-id="9951f-122">Description</span><span class="sxs-lookup"><span data-stu-id="9951f-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="9951f-123">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="9951f-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="9951f-124">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9951f-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9951f-125">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="9951f-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9951f-126">Notes</span><span class="sxs-lookup"><span data-stu-id="9951f-126">Remarks</span></span>  
 <span data-ttu-id="9951f-127">Appel de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> méthode à l’aide des noms d’assemblys partiels provoque le common language runtime à rechercher l’assembly uniquement dans le répertoire de base d’application.</span><span class="sxs-lookup"><span data-stu-id="9951f-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="9951f-128">Utilisez le  **\<qualifyAssembly >** élément dans votre fichier de configuration d’application pour fournir les informations d’assembly complet (nom, version, jeton de clé publique et culture) et forcer le common language runtime à rechercher l’assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="9951f-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="9951f-129">Le **fullName** attribut doit inclure les quatre champs d’identité de l’assembly : nom, version, jeton de clé publique et culture.</span><span class="sxs-lookup"><span data-stu-id="9951f-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="9951f-130">Le **partialName** attribut doit référencer partiellement un assembly.</span><span class="sxs-lookup"><span data-stu-id="9951f-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="9951f-131">Vous devez spécifier au moins le nom de texte de l’assembly (le cas le plus courant), mais vous pouvez également inclure la version, jeton de clé publique, ou de culture (ou n’importe quelle combinaison de quatre, mais pas les quatre).</span><span class="sxs-lookup"><span data-stu-id="9951f-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="9951f-132">Le **partialName** doit correspondre au nom spécifié dans votre appel.</span><span class="sxs-lookup"><span data-stu-id="9951f-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="9951f-133">Par exemple, vous ne pouvez pas spécifier `"math"` comme le **partialName** attribut dans votre fichier de configuration et l’appel `Assembly.Load("math, Version=3.3.3.3")` dans votre code.</span><span class="sxs-lookup"><span data-stu-id="9951f-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9951f-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="9951f-134">Example</span></span>  
 <span data-ttu-id="9951f-135">L’exemple suivant transforme logiquement l’appel `Assembly.Load("math")` dans `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="9951f-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9951f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9951f-136">See Also</span></span>  
 [<span data-ttu-id="9951f-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="9951f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="9951f-138">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="9951f-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="9951f-139">NIB : Références d’Assembly partielles</span><span class="sxs-lookup"><span data-stu-id="9951f-139">NIB: Partial Assembly References</span></span>](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
