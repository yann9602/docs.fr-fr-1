---
title: "&lt;System.CodeDom&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8b223ab6ab742c5b7d3b3d2f5640e99835afe268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="a1182-102">&lt;System.CodeDom&gt; élément</span><span class="sxs-lookup"><span data-stu-id="a1182-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="a1182-103">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="a1182-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="a1182-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="a1182-104">\<configuration> Element</span></span>  
<span data-ttu-id="a1182-105">\<System.CodeDom > élément</span><span class="sxs-lookup"><span data-stu-id="a1182-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1182-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1182-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1182-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a1182-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a1182-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a1182-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1182-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a1182-109">Attributes</span></span>  
 <span data-ttu-id="a1182-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="a1182-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1182-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a1182-111">Child Elements</span></span>  
  
|<span data-ttu-id="a1182-112">Élément</span><span class="sxs-lookup"><span data-stu-id="a1182-112">Element</span></span>|<span data-ttu-id="a1182-113">Description</span><span class="sxs-lookup"><span data-stu-id="a1182-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1182-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="a1182-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="a1182-115">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="a1182-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1182-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a1182-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a1182-117">Élément</span><span class="sxs-lookup"><span data-stu-id="a1182-117">Element</span></span>|<span data-ttu-id="a1182-118">Description</span><span class="sxs-lookup"><span data-stu-id="a1182-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1182-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a1182-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a1182-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1182-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1182-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1182-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="a1182-122">.NET framework Version 2.0</span><span class="sxs-lookup"><span data-stu-id="a1182-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="a1182-123">Le [ \<system.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) élément contient des paramètres de configuration de compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut sont installés avec le .NET Framework, tel que le <xref:Microsoft.CSharp.CSharpCodeProvider> et <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="a1182-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="a1182-124">Le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément contient zéro ou plusieurs [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="a1182-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="a1182-125">Chaque [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.</span><span class="sxs-lookup"><span data-stu-id="a1182-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a1182-126">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur (Machine.config) pour une nouvelle <xref:System.CodeDom.Compiler.CodeDomProvider> implémentation.</span><span class="sxs-lookup"><span data-stu-id="a1182-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a1182-127">Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a1182-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1182-128">Dans les versions du .NET Framework 1.0 et 1.1, la langue par défaut fournisseurs fournis par le .NET Framework sont identifiées dans le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="a1182-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="a1182-129">Dans le .NET Framework version 2.0, les fournisseurs de langages par défaut ne sont pas identifiées dans le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément, mais peuvent être énumérés à l’aide de la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="a1182-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="a1182-130">Versions 1.0 et 1.1 du .NET framework</span><span class="sxs-lookup"><span data-stu-id="a1182-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="a1182-131">Le [ \<system.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a1182-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="a1182-132">Le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément contient zéro ou plusieurs [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="a1182-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="a1182-133">Chaque [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.</span><span class="sxs-lookup"><span data-stu-id="a1182-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a1182-134">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a1182-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a1182-135">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="a1182-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a1182-136">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a1182-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a1182-137">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="a1182-137">Configuration File</span></span>  
 <span data-ttu-id="a1182-138">Cet élément peut être utilisé dans le fichier de configuration machine et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="a1182-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1182-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1182-139">Example</span></span>  
 <span data-ttu-id="a1182-140">L’exemple suivant illustre une configuration de compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="a1182-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1182-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1182-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="a1182-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a1182-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a1182-143">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="a1182-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="a1182-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="a1182-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
