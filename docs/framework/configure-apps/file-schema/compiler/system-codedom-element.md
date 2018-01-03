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
ms.workload: dotnet
ms.openlocfilehash: bf2e041f9ae9661a9b6f8ecd5883ac7d1b0f0dec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="27355-102">&lt;System.CodeDom&gt; élément</span><span class="sxs-lookup"><span data-stu-id="27355-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="27355-103">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="27355-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="27355-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="27355-104">\<configuration> Element</span></span>  
<span data-ttu-id="27355-105">\<System.CodeDom > élément</span><span class="sxs-lookup"><span data-stu-id="27355-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27355-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27355-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27355-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="27355-107">Attributes and Elements</span></span>  
 <span data-ttu-id="27355-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="27355-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27355-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="27355-109">Attributes</span></span>  
 <span data-ttu-id="27355-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="27355-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27355-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27355-111">Child Elements</span></span>  
  
|<span data-ttu-id="27355-112">Élément</span><span class="sxs-lookup"><span data-stu-id="27355-112">Element</span></span>|<span data-ttu-id="27355-113">Description</span><span class="sxs-lookup"><span data-stu-id="27355-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27355-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="27355-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="27355-115">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="27355-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27355-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27355-116">Parent Elements</span></span>  
  
|<span data-ttu-id="27355-117">Élément</span><span class="sxs-lookup"><span data-stu-id="27355-117">Element</span></span>|<span data-ttu-id="27355-118">Description</span><span class="sxs-lookup"><span data-stu-id="27355-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27355-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="27355-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="27355-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27355-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27355-121">Notes</span><span class="sxs-lookup"><span data-stu-id="27355-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="27355-122">.NET framework Version 2.0</span><span class="sxs-lookup"><span data-stu-id="27355-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="27355-123">Le [ \<system.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) élément contient des paramètres de configuration de compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut sont installés avec le .NET Framework, tel que le <xref:Microsoft.CSharp.CSharpCodeProvider> et <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="27355-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="27355-124">Le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément contient zéro ou plusieurs [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="27355-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="27355-125">Chaque [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.</span><span class="sxs-lookup"><span data-stu-id="27355-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="27355-126">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur (Machine.config) pour une nouvelle <xref:System.CodeDom.Compiler.CodeDomProvider> implémentation.</span><span class="sxs-lookup"><span data-stu-id="27355-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="27355-127">Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="27355-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27355-128">Dans les versions du .NET Framework 1.0 et 1.1, la langue par défaut fournisseurs fournis par le .NET Framework sont identifiées dans le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="27355-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="27355-129">Dans le .NET Framework version 2.0, les fournisseurs de langages par défaut ne sont pas identifiées dans le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément, mais peuvent être énumérés à l’aide de la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="27355-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="27355-130">Versions 1.0 et 1.1 du .NET framework</span><span class="sxs-lookup"><span data-stu-id="27355-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="27355-131">Le [ \<system.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="27355-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="27355-132">Le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément contient zéro ou plusieurs [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="27355-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="27355-133">Chaque [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.</span><span class="sxs-lookup"><span data-stu-id="27355-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="27355-134">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="27355-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="27355-135">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="27355-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="27355-136">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="27355-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="27355-137">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="27355-137">Configuration File</span></span>  
 <span data-ttu-id="27355-138">Cet élément peut être utilisé dans le fichier de configuration machine et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="27355-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27355-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="27355-139">Example</span></span>  
 <span data-ttu-id="27355-140">L’exemple suivant illustre une configuration de compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="27355-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27355-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27355-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="27355-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="27355-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="27355-143">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="27355-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="27355-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="27355-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
