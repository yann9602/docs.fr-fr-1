---
title: "&lt;compilateur&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8d2562bb37413cd07b4548bbf2bad0b6a9aedbc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="13ac5-102">&lt;compilateur&gt; élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="13ac5-103">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="13ac5-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="13ac5-104">\<Élément de configuration ></span><span class="sxs-lookup"><span data-stu-id="13ac5-104">\<configuration Element></span></span>  
<span data-ttu-id="13ac5-105">\<System.CodeDom (élément) ></span><span class="sxs-lookup"><span data-stu-id="13ac5-105">\<system.codedom Element></span></span>  
<span data-ttu-id="13ac5-106">\<compilateurs élément ></span><span class="sxs-lookup"><span data-stu-id="13ac5-106">\<compilers Element></span></span>  
<span data-ttu-id="13ac5-107">\<compilateur > élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ac5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13ac5-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13ac5-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="13ac5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13ac5-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="13ac5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13ac5-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="13ac5-111">Attributes</span></span>  
  
|<span data-ttu-id="13ac5-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="13ac5-112">Attribute</span></span>|<span data-ttu-id="13ac5-113">Description</span><span class="sxs-lookup"><span data-stu-id="13ac5-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="13ac5-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="13ac5-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="13ac5-115">Spécifie des arguments supplémentaires spécifiques au compilateur pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="13ac5-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="13ac5-116">Les valeurs pour le `compilerOptions` attribut sont généralement répertoriées dans une rubrique d’options du compilateur pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="13ac5-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="13ac5-117">Dans la documentation de Visual Studio 2005, vous pouvez localiser les options du compilateur en recherchant « options du compilateur » dans l’index.</span><span class="sxs-lookup"><span data-stu-id="13ac5-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="13ac5-118">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="13ac5-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="13ac5-119">Fournit une liste délimitée par des points-virgules des extensions de nom de fichier utilisé par les fichiers sources pour le fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="13ac5-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="13ac5-120">Par exemple, « .cs ».</span><span class="sxs-lookup"><span data-stu-id="13ac5-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="13ac5-121">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="13ac5-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="13ac5-122">Fournit une liste délimitée par des points-virgules de noms de langages pris en charge par le fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="13ac5-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="13ac5-123">Par exemple, « c# ; cs ; csharp ».</span><span class="sxs-lookup"><span data-stu-id="13ac5-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="13ac5-124">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="13ac5-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="13ac5-125">Spécifie le nom de type du fournisseur de langage, y compris le nom de l’assembly contenant l’implémentation du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="13ac5-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="13ac5-126">Le nom de type doit respecter les exigences définies dans [en spécifiant des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="13ac5-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="13ac5-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="13ac5-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="13ac5-128">Spécifie le niveau d’avertissement du compilateur par défaut ; Détermine le niveau auquel le fournisseur de langage traite les avertissements de compilation comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="13ac5-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13ac5-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="13ac5-129">Child Elements</span></span>  
  
|<span data-ttu-id="13ac5-130">Élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-130">Element</span></span>|<span data-ttu-id="13ac5-131">Description</span><span class="sxs-lookup"><span data-stu-id="13ac5-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13ac5-132">\<providerOption > élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="13ac5-133">Spécifie les attributs de version du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="13ac5-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13ac5-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="13ac5-134">Parent Elements</span></span>  
  
|<span data-ttu-id="13ac5-135">Élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-135">Element</span></span>|<span data-ttu-id="13ac5-136">Description</span><span class="sxs-lookup"><span data-stu-id="13ac5-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13ac5-137">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="13ac5-138">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13ac5-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="13ac5-139">\<System.CodeDom > élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="13ac5-140">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="13ac5-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="13ac5-141">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="13ac5-142">Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs `<compiler>` éléments.</span><span class="sxs-lookup"><span data-stu-id="13ac5-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13ac5-143">Remarques</span><span class="sxs-lookup"><span data-stu-id="13ac5-143">Remarks</span></span>  
 <span data-ttu-id="13ac5-144">Chaque `<compiler>` élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.</span><span class="sxs-lookup"><span data-stu-id="13ac5-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="13ac5-145">Le fournisseur étend la <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> classe pour une langue spécifique ; la `<compiler>` élément définit les paramètres de générateur de code pour le fournisseur de langage et le compilateur.</span><span class="sxs-lookup"><span data-stu-id="13ac5-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="13ac5-146">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="13ac5-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="13ac5-147">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="13ac5-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="13ac5-148">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="13ac5-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="13ac5-149">Éléments du compilateur dans l’application ou le fichier de configuration Web peuvent compléter ou remplacer les paramètres dans le fichier de configuration machine.</span><span class="sxs-lookup"><span data-stu-id="13ac5-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="13ac5-150">Si plusieurs implémentations de fournisseur sont configurée pour le même nom de la langue ou la même extension de fichier, la dernière configuration correspondante remplace tous les fournisseurs configurés précédentes pour cette extension de fichier ou le nom de langue.</span><span class="sxs-lookup"><span data-stu-id="13ac5-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="13ac5-151">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="13ac5-151">Configuration File</span></span>  
 <span data-ttu-id="13ac5-152">Cet élément peut être utilisé dans le fichier de configuration machine et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="13ac5-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ac5-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="13ac5-153">Example</span></span>  
 <span data-ttu-id="13ac5-154">L’exemple suivant illustre un élément de configuration du compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="13ac5-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ac5-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13ac5-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="13ac5-156">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="13ac5-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="13ac5-157">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="13ac5-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="13ac5-158">Spécification des noms de types complets</span><span class="sxs-lookup"><span data-stu-id="13ac5-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="13ac5-159">compilateur, élément pour les compilateurs pour compilation (schéma des paramètres ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="13ac5-159">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
