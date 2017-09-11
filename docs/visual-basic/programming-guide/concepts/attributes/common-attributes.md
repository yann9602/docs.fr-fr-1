---
title: Attributs courants (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9adb5cb378701c8d06a3fa28bad44dc857026b5a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="5a495-102">Attributs courants (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a495-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="5a495-103">Cette rubrique décrit les attributs qui sont couramment utilisés dans les programmes Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a495-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="5a495-104">Attributs globaux</span><span class="sxs-lookup"><span data-stu-id="5a495-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="5a495-105">Attribut obsolète</span><span class="sxs-lookup"><span data-stu-id="5a495-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="5a495-106">Attribut conditionnel</span><span class="sxs-lookup"><span data-stu-id="5a495-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="5a495-107">Attributs d’informations de l’appelant</span><span class="sxs-lookup"><span data-stu-id="5a495-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="5a495-108">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a495-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <span data-ttu-id="5a495-109"><a name="Global"></a>Attributs globaux</span><span class="sxs-lookup"><span data-stu-id="5a495-109"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="5a495-110">La plupart des attributs sont appliqués aux éléments de langage spécifiques telles que les classes ou méthodes ; Toutefois, certains attributs sont globaux — ils s’appliquent à un assembly entier ou un module.</span><span class="sxs-lookup"><span data-stu-id="5a495-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="5a495-111">Par exemple, le <xref:System.Reflection.AssemblyVersionAttribute>attribut peut être utilisé pour incorporer les informations de version dans un assembly, comme suit :</xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="5a495-112">Les attributs globaux apparaissent dans le code source après chaque niveau supérieur`Imports` instructions et avant les déclarations de type, de module ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5a495-112">Global attributes appear in the source code after any top-level`Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="5a495-113">Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage.</span><span class="sxs-lookup"><span data-stu-id="5a495-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="5a495-114">Pour les projets Visual Basic, les attributs globaux sont généralement placés dans le fichier AssemblyInfo.vb (le fichier est créé automatiquement lorsque vous créez un projet dans Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="5a495-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="5a495-115">Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="5a495-116">Elles se répartissent dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a495-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="5a495-117">Attributs d’identité assembly</span><span class="sxs-lookup"><span data-stu-id="5a495-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="5a495-118">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="5a495-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="5a495-119">Attributs de manifeste d’assembly</span><span class="sxs-lookup"><span data-stu-id="5a495-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="5a495-120">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="5a495-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="5a495-121">Trois attributs (avec un nom fort, le cas échéant) déterminent l’identité d’un assembly : nom, version et culture.</span><span class="sxs-lookup"><span data-stu-id="5a495-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="5a495-122">Ces attributs constituent le nom complet de l’assembly et sont requis lorsque vous faites référence dans le code.</span><span class="sxs-lookup"><span data-stu-id="5a495-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="5a495-123">Vous pouvez définir la version et la culture à l’aide des attributs d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="5a495-124">Toutefois, la valeur de nom est définie par le compilateur, l’IDE de Visual Studio dans le [boîte de dialogue Informations Assembly](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), ou l’utilitaire Assembly Linker (Al.exe) lorsque l’assembly est créé, basé sur le fichier qui contient le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="5a495-125">Le <xref:System.Reflection.AssemblyFlagsAttribute>attribut détermine si plusieurs copies de l’assembly peuvent coexister.</xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="5a495-126">Le tableau suivant montre les attributs d’identité.</span><span class="sxs-lookup"><span data-stu-id="5a495-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="5a495-127">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a495-127">Attribute</span></span>|<span data-ttu-id="5a495-128">Objectif</span><span class="sxs-lookup"><span data-stu-id="5a495-128">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5a495-129"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="5a495-129"><xref:System.Reflection.AssemblyName></span></span>|<span data-ttu-id="5a495-130">Décrit intégralement l’identité d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-130">Fully describes the identity of an assembly.</span></span>|  
|<span data-ttu-id="5a495-131"><xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-131"><xref:System.Reflection.AssemblyVersionAttribute></span></span>|<span data-ttu-id="5a495-132">Spécifie la version d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-132">Specifies the version of an assembly.</span></span>|  
|<span data-ttu-id="5a495-133"><xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-133"><xref:System.Reflection.AssemblyCultureAttribute></span></span>|<span data-ttu-id="5a495-134">Spécifie la culture prise en charge par l'assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-134">Specifies which culture the assembly supports.</span></span>|  
|<span data-ttu-id="5a495-135"><xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-135"><xref:System.Reflection.AssemblyFlagsAttribute></span></span>|<span data-ttu-id="5a495-136">Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5a495-136">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="5a495-137">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="5a495-137">Informational Attributes</span></span>  
 <span data-ttu-id="5a495-138">Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-138">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="5a495-139">Le tableau suivant répertorie les attributs d’informations définis dans le <xref:System.Reflection?displayProperty=fullName>espace de noms.</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5a495-139">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="5a495-140">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a495-140">Attribute</span></span>|<span data-ttu-id="5a495-141">Objectif</span><span class="sxs-lookup"><span data-stu-id="5a495-141">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5a495-142"><xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-142"><xref:System.Reflection.AssemblyProductAttribute></span></span>|<span data-ttu-id="5a495-143">Définit un attribut personnalisé qui spécifie un nom de produit pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-143">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-144"><xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-144"><xref:System.Reflection.AssemblyTrademarkAttribute></span></span>|<span data-ttu-id="5a495-145">Définit un attribut personnalisé qui spécifie une marque pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-145">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></span></span>|<span data-ttu-id="5a495-147">Définit un attribut personnalisé qui spécifie une version d’informations pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-147">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-148"><xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-148"><xref:System.Reflection.AssemblyCompanyAttribute></span></span>|<span data-ttu-id="5a495-149">Définit un attribut personnalisé qui spécifie un nom de société pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-149">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-150"><xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-150"><xref:System.Reflection.AssemblyCopyrightAttribute></span></span>|<span data-ttu-id="5a495-151">Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-151">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-152"><xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-152"><xref:System.Reflection.AssemblyFileVersionAttribute></span></span>|<span data-ttu-id="5a495-153">Indique au compilateur d’utiliser un numéro de version spécifique pour la ressource de version de fichier Win32.</span><span class="sxs-lookup"><span data-stu-id="5a495-153">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<span data-ttu-id="5a495-154"><xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-154"><xref:System.CLSCompliantAttribute></span></span>|<span data-ttu-id="5a495-155">Indique si l’assembly est compatible avec le Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="5a495-155">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="5a495-156">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="5a495-156">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="5a495-157">Vous pouvez utiliser les attributs de manifeste d’assembly pour fournir des informations dans le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-157">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="5a495-158">Cela inclut le titre, description, alias par défaut et configuration.</span><span class="sxs-lookup"><span data-stu-id="5a495-158">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="5a495-159">Le tableau suivant présente les attributs de manifeste d’assembly définis dans le <xref:System.Reflection?displayProperty=fullName>espace de noms.</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5a495-159">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="5a495-160">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a495-160">Attribute</span></span>|<span data-ttu-id="5a495-161">Objectif</span><span class="sxs-lookup"><span data-stu-id="5a495-161">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5a495-162"><xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-162"><xref:System.Reflection.AssemblyTitleAttribute></span></span>|<span data-ttu-id="5a495-163">Définit un attribut personnalisé qui spécifie un titre d’assembly pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-163">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-164"><xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-164"><xref:System.Reflection.AssemblyDescriptionAttribute></span></span>|<span data-ttu-id="5a495-165">Définit un attribut personnalisé qui spécifie une description de l’assembly pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-165">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-166"><xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-166"><xref:System.Reflection.AssemblyConfigurationAttribute></span></span>|<span data-ttu-id="5a495-167">Définit un attribut personnalisé qui spécifie une configuration de l’assembly (par exemple, retail ou debug) pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5a495-167">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<span data-ttu-id="5a495-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></span></span>|<span data-ttu-id="5a495-169">Définit un alias par défaut convivial pour un manifeste d’assembly</span><span class="sxs-lookup"><span data-stu-id="5a495-169">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="5a495-170"><a name="Obsolete"></a>Attribut obsolète</span><span class="sxs-lookup"><span data-stu-id="5a495-170"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="5a495-171">Le `Obsolete` attribut marque une entité de programme qui n’est plus recommandé pour une utilisation.</span><span class="sxs-lookup"><span data-stu-id="5a495-171">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="5a495-172">Chaque utilisation d’une entité désignée comme obsolète génère par la suite un avertissement ou une erreur, selon la configuration de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="5a495-172">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="5a495-173">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5a495-173">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5a495-174">Dans cet exemple la `Obsolete` attribut est appliqué à la classe `A` et à la méthode `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="5a495-174">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="5a495-175">Étant donné que le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a `true`, cette méthode entraîne une erreur du compilateur, alors qu’à l’aide de la classe `A` n’entraîne qu’un avertissement.</span><span class="sxs-lookup"><span data-stu-id="5a495-175">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="5a495-176">Appel de `B.NewMethod`, toutefois, ne produit aucun avertissement ni erreur.</span><span class="sxs-lookup"><span data-stu-id="5a495-176">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="5a495-177">La chaîne fournie comme premier argument au constructeur d’attribut s’affichera dans le cadre de l’avertissement ou l’erreur.</span><span class="sxs-lookup"><span data-stu-id="5a495-177">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="5a495-178">Par exemple, lorsque vous l’utilisez avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :</span><span class="sxs-lookup"><span data-stu-id="5a495-178">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="5a495-179">Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="5a495-179">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="5a495-180">Le `Obsolete` attribut peut être utilisé sans arguments, mais y compris les raisons de l’élément est obsolète et est recommandé d’utiliser à la place.</span><span class="sxs-lookup"><span data-stu-id="5a495-180">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="5a495-181">Le `Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs.</span><span class="sxs-lookup"><span data-stu-id="5a495-181">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="5a495-182">`Obsolete`est un alias pour <xref:System.ObsoleteAttribute>.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-182">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="5a495-183"><a name="Conditional"></a>Attribut conditionnel</span><span class="sxs-lookup"><span data-stu-id="5a495-183"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="5a495-184">Le `Conditional` attribut rend l’exécution d’une méthode dépendante d’un identificateur de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="5a495-184">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="5a495-185">Le `Conditional` l’attribut est un alias pour <xref:System.Diagnostics.ConditionalAttribute>et peut être appliqué à une méthode ou une classe d’attribut</xref:System.Diagnostics.ConditionalAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-185">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="5a495-186">Dans cet exemple, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage des informations de diagnostic spécifiques au programme :</span><span class="sxs-lookup"><span data-stu-id="5a495-186">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5a495-187">Si le `TRACE_ON` identificateur n’est pas défini, aucune sortie de trace ne s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5a495-187">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="5a495-188">Le `Conditional` attribut est souvent utilisé avec le `DEBUG` identificateur pour activer la trace et enregistrer des fonctionnalités pour les versions debug, mais pas de versions, comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a495-188">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="5a495-189">Lorsqu’une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="5a495-189">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="5a495-190">Si le symbole est défini, l’appel est inclus ; dans le cas contraire, l’appel est omis.</span><span class="sxs-lookup"><span data-stu-id="5a495-190">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="5a495-191">À l’aide de `Conditional` est un nettoyeur, alternative plus élégante et moins sujette aux erreurs méthodes englobantes `#if…#endif` blocs, comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a495-191">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="5a495-192">Une méthode conditionnelle doit être une méthode dans une déclaration de classe ou un struct et ne doit pas avoir une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="5a495-192">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="5a495-193">Utilisation de plusieurs identificateurs</span><span class="sxs-lookup"><span data-stu-id="5a495-193">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="5a495-194">Si une méthode comporte plusieurs `Conditional` attributs, un appel à la méthode est inclus si un des symboles conditionnels au moins est défini (en d’autres termes, les symboles sont liés logiquement à l’aide de l’opérateur OR).</span><span class="sxs-lookup"><span data-stu-id="5a495-194">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="5a495-195">Dans cet exemple, la présence de `A` ou `B` entraîne un appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="5a495-195">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="5a495-196">Pour obtenir l’effet de lier logiquement les symboles à l’aide de l’opérateur AND, vous pouvez définir des méthodes conditionnelles en série.</span><span class="sxs-lookup"><span data-stu-id="5a495-196">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="5a495-197">Par exemple, la deuxième méthode ci-dessous exécutera uniquement si `A` et `B` sont définis :</span><span class="sxs-lookup"><span data-stu-id="5a495-197">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="5a495-198">Utilisation du conditionnel avec les Classes d’attributs</span><span class="sxs-lookup"><span data-stu-id="5a495-198">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="5a495-199">Le `Conditional` attribut peut également être appliqué à une définition de classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="5a495-199">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="5a495-200">Dans cet exemple, l’attribut personnalisé `Documentation` n’ajoute des informations aux métadonnées si DEBUG est défini.</span><span class="sxs-lookup"><span data-stu-id="5a495-200">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <span data-ttu-id="5a495-201"><a name="CallerInfo"></a>Attributs d’informations de l’appelant</span><span class="sxs-lookup"><span data-stu-id="5a495-201"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="5a495-202">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="5a495-202">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="5a495-203">Vous pouvez obtenir le chemin d’accès du code source, le numéro de ligne dans le code source et le nom du membre de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="5a495-203">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="5a495-204">Pour obtenir des informations sur le membre appelant, vous utilisez des attributs qui sont appliqués aux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="5a495-204">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="5a495-205">Chaque paramètre facultatif spécifie une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a495-205">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="5a495-206">Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définies dans le <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms :</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5a495-206">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="5a495-207">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a495-207">Attribute</span></span>|<span data-ttu-id="5a495-208">Description</span><span class="sxs-lookup"><span data-stu-id="5a495-208">Description</span></span>|<span data-ttu-id="5a495-209">Type</span><span class="sxs-lookup"><span data-stu-id="5a495-209">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="5a495-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="5a495-211">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="5a495-211">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="5a495-212">C’est le chemin d’accès au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="5a495-212">This is the path at compile time.</span></span>|`String`|  
|<span data-ttu-id="5a495-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="5a495-214">Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="5a495-214">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="5a495-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="5a495-216">Nom de la méthode ou propriété de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="5a495-216">Method name or property name of the caller.</span></span> <span data-ttu-id="5a495-217">Pour plus d’informations, consultez [les informations de l’appelant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="5a495-217">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="5a495-218">Pour plus d’informations sur les attributs d’informations de l’appelant, consultez [les informations de l’appelant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="5a495-218">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <span data-ttu-id="5a495-219"><a name="VB"></a>Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a495-219"><a name="VB"></a> Visual Basic Attributes</span></span>  
 <span data-ttu-id="5a495-220">Le tableau suivant répertorie les attributs qui sont spécifiques à Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a495-220">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="5a495-221">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a495-221">Attribute</span></span>|<span data-ttu-id="5a495-222">Objectif</span><span class="sxs-lookup"><span data-stu-id="5a495-222">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5a495-223"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-223"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>|<span data-ttu-id="5a495-224">Indique au compilateur que la classe doit être exposée comme un objet COM.</span><span class="sxs-lookup"><span data-stu-id="5a495-224">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<span data-ttu-id="5a495-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></span></span>|<span data-ttu-id="5a495-226">Permet d’accéder à l’aide uniquement de la qualification nécessaire pour le module aux membres de module.</span><span class="sxs-lookup"><span data-stu-id="5a495-226">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<span data-ttu-id="5a495-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></span></span>|<span data-ttu-id="5a495-228">Spécifie la taille d’une chaîne de longueur fixe dans une structure à utiliser avec le fichier d’entrée et sortie fonctions.</span><span class="sxs-lookup"><span data-stu-id="5a495-228">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<span data-ttu-id="5a495-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span><span class="sxs-lookup"><span data-stu-id="5a495-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span></span>|<span data-ttu-id="5a495-230">Spécifie la taille d’un tableau fixe dans une structure à utiliser avec le fichier d’entrée et sortie fonctions.</span><span class="sxs-lookup"><span data-stu-id="5a495-230">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="5a495-231">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="5a495-231">COMClassAttribute</span></span>  
 <span data-ttu-id="5a495-232">Utilisez `COMClassAttribute` pour simplifier le processus de création de composants COM à partir de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a495-232">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="5a495-233">Les objets COM sont très différents des assemblys .NET Framework et sans `COMClassAttribute`, vous devez suivre un certain nombre d’étapes pour générer un objet COM à partir de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a495-233">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="5a495-234">Pour les classes marquées avec `COMClassAttribute`, le compilateur effectue la plupart de ces étapes automatiquement.</span><span class="sxs-lookup"><span data-stu-id="5a495-234">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="5a495-235">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="5a495-235">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="5a495-236">Utilisez `HideModuleNameAttribute` pour autoriser les membres de module d’être accessibles à l’aide uniquement de la qualification nécessaire pour le module.</span><span class="sxs-lookup"><span data-stu-id="5a495-236">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="5a495-237">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="5a495-237">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="5a495-238">Utilisez `VBFixedStringAttribute` pour forcer Visual Basic pour créer une chaîne de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="5a495-238">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="5a495-239">Sont des chaînes de longueur variable par défaut, et cet attribut est utile pour stocker des chaînes dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a495-239">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="5a495-240">Le code suivant illustre cela :</span><span class="sxs-lookup"><span data-stu-id="5a495-240">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="5a495-241">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="5a495-241">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="5a495-242">Utilisez `VBFixedArrayAttribute` pour déclarer des tableaux de taille fixe.</span><span class="sxs-lookup"><span data-stu-id="5a495-242">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="5a495-243">Comme les chaînes Visual Basic, les tableaux sont de longueur variable par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a495-243">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="5a495-244">Cet attribut est utile lors de la sérialisation ou écrire des données dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a495-244">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a495-245">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a495-245">See Also</span></span>  
 <span data-ttu-id="5a495-246"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="5a495-246"><xref:System.Reflection></span></span>   
 <span data-ttu-id="5a495-247"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="5a495-247"><xref:System.Attribute></span></span>   
<span data-ttu-id="5a495-248"> [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a495-248"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="5a495-249"> [Attributs](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="5a495-249"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="5a495-250"> [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="5a495-250"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="5a495-251"> [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="5a495-251"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
