---
title: "&lt;compilateurs&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: deb9f99253c4cf523c8fe5052b1f30823e5e9944
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="800d9-102">&lt;compilateurs&gt; élément</span><span class="sxs-lookup"><span data-stu-id="800d9-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="800d9-103">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="800d9-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="800d9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="800d9-104">\<configuration></span></span>  
<span data-ttu-id="800d9-105">\<System.CodeDom ></span><span class="sxs-lookup"><span data-stu-id="800d9-105">\<system.codedom></span></span>  
<span data-ttu-id="800d9-106">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="800d9-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="800d9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="800d9-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="800d9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="800d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="800d9-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="800d9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="800d9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="800d9-110">Attributes</span></span>  
 <span data-ttu-id="800d9-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="800d9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="800d9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="800d9-112">Child Elements</span></span>  
  
|<span data-ttu-id="800d9-113">Élément</span><span class="sxs-lookup"><span data-stu-id="800d9-113">Element</span></span>|<span data-ttu-id="800d9-114">Description</span><span class="sxs-lookup"><span data-stu-id="800d9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="800d9-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="800d9-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="800d9-116">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="800d9-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="800d9-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="800d9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="800d9-118">Élément</span><span class="sxs-lookup"><span data-stu-id="800d9-118">Element</span></span>|<span data-ttu-id="800d9-119">Description</span><span class="sxs-lookup"><span data-stu-id="800d9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="800d9-120">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="800d9-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="800d9-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="800d9-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="800d9-122">\<System.CodeDom > élément</span><span class="sxs-lookup"><span data-stu-id="800d9-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="800d9-123">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="800d9-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="800d9-124">Notes</span><span class="sxs-lookup"><span data-stu-id="800d9-124">Remarks</span></span>  
 <span data-ttu-id="800d9-125">Le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="800d9-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="800d9-126">Chaque [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.</span><span class="sxs-lookup"><span data-stu-id="800d9-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="800d9-127">Le .NET Framework définit les paramètres du fournisseur de langage du compilateur initial dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="800d9-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="800d9-128">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="800d9-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="800d9-129">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="800d9-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="800d9-130">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="800d9-130">Configuration File</span></span>  
 <span data-ttu-id="800d9-131">Cet élément peut être utilisé dans le fichier de configuration machine et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="800d9-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="800d9-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="800d9-132">Example</span></span>  
 <span data-ttu-id="800d9-133">L’exemple suivant illustre un élément de configuration du compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="800d9-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="800d9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="800d9-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="800d9-135">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="800d9-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="800d9-136">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="800d9-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="800d9-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="800d9-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
