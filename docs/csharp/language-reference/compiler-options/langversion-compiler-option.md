---
title: -langversion (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /langversion
dev_langs:
- CSharp
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fc501c5532d27168d74d1a5f293abe59d3beeef1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="langversion-c-compiler-options"></a><span data-ttu-id="661a7-102">/langversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="661a7-102">/langversion (C# Compiler Options)</span></span>
<span data-ttu-id="661a7-103">Force le compilateur à accepter uniquement la syntaxe incluse dans la spécification choisie du langage C#.</span><span class="sxs-lookup"><span data-stu-id="661a7-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="661a7-104">Syntax</span></span>  
  
```console  
/langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="661a7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="661a7-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="661a7-106">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="661a7-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="661a7-107">Option</span><span class="sxs-lookup"><span data-stu-id="661a7-107">Option</span></span>|<span data-ttu-id="661a7-108">Signification</span><span class="sxs-lookup"><span data-stu-id="661a7-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="661a7-109">default</span><span class="sxs-lookup"><span data-stu-id="661a7-109">default</span></span>|<span data-ttu-id="661a7-110">Le compilateur accepte toute la syntaxe de langage valide qu’il peut prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="661a7-110">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="661a7-111"><sup id="TDefault">[Default](#FDefault)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-111"><sup id="TDefault">[Default](#FDefault)</sup></span></span>| 
|<span data-ttu-id="661a7-112">ISO-1</span><span class="sxs-lookup"><span data-stu-id="661a7-112">ISO-1</span></span>|<span data-ttu-id="661a7-113">Le compilateur accepte uniquement la syntaxe qui est incluse dans ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-113">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="661a7-114">ISO-2</span><span class="sxs-lookup"><span data-stu-id="661a7-114">ISO-2</span></span>|<span data-ttu-id="661a7-115">Le compilateur accepte uniquement la syntaxe qui est incluse dans ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-115">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="661a7-116">3</span><span class="sxs-lookup"><span data-stu-id="661a7-116">3</span></span>|<span data-ttu-id="661a7-117">Le compilateur accepte uniquement la syntaxe qui est incluse dans C# version 3.0 ou inférieure <sup id="TCS3">[CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-117">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="661a7-118">4</span><span class="sxs-lookup"><span data-stu-id="661a7-118">4</span></span>|<span data-ttu-id="661a7-119">Le compilateur accepte uniquement la syntaxe qui est incluse dans C# version 4.0 ou inférieure <sup id="TCS4">[CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-119">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="661a7-120">5</span><span class="sxs-lookup"><span data-stu-id="661a7-120">5</span></span>|<span data-ttu-id="661a7-121">Le compilateur accepte uniquement la syntaxe qui est incluse dans C# version 5.0 ou inférieure <sup id="TCS5">[CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-121">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="661a7-122">6</span><span class="sxs-lookup"><span data-stu-id="661a7-122">6</span></span>|<span data-ttu-id="661a7-123">Le compilateur accepte uniquement la syntaxe qui est incluse dans C# version 6.0 ou inférieure <sup id="TCS6">[CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-123">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="661a7-124">7</span><span class="sxs-lookup"><span data-stu-id="661a7-124">7</span></span>|<span data-ttu-id="661a7-125">Le compilateur accepte uniquement la syntaxe qui est incluse dans C# version 7.0 ou inférieure <sup id="TCS7">[CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-125">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="661a7-126">latest</span><span class="sxs-lookup"><span data-stu-id="661a7-126">latest</span></span>|<span data-ttu-id="661a7-127">Le compilateur accepte toute la syntaxe de langage valide qu’il peut prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="661a7-127">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="661a7-128"><sup id="TLatest">[Latest](#FLatest)</sup></span><span class="sxs-lookup"><span data-stu-id="661a7-128"><sup id="TLatest">[Latest](#FLatest)</sup></span></span>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="661a7-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="661a7-129">Remarks</span></span>  
 <span data-ttu-id="661a7-130">Les métadonnées référencées par votre application C# ne sont pas visées par l’option de compilateur **/langversion**.</span><span class="sxs-lookup"><span data-stu-id="661a7-130">Metadata referenced by your C# application is not subject to **/langversion** compiler option.</span></span>  
  
 <span data-ttu-id="661a7-131">Sachant que chaque version du compilateur C# contient des extensions de la spécification du langage, **/langversion** ne vous offre pas les fonctionnalités équivalentes d’une version antérieure du compilateur.</span><span class="sxs-lookup"><span data-stu-id="661a7-131">Because each version of the C# compiler contains extensions to the language specification, **/langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="661a7-132">De plus, alors que les mises à jour de la version de C# coïncident généralement avec la publication des principales versions du .NET Framework, la nouvelle syntaxe et les nouvelles fonctionnalités ne sont pas nécessairement liées à cette version spécifique du framework.</span><span class="sxs-lookup"><span data-stu-id="661a7-132">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="661a7-133">Alors que les nouvelles fonctionnalités nécessiteront certainement une nouvelle mise à jour du compilateur qui sera publiée en même temps que la révision de C#, chaque fonctionnalité spécifique exigera une configuration minimale pour les API .NET ou le common language runtime qui pourra lui permettre de s’exécuter sur des frameworks de bas niveau moyennant des packages NuGet ou d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="661a7-133">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="661a7-134">Quel que soit le paramètre **/langversion** que vous utiliserez, vous vous servirez de la version active du common language runtime pour créer votre fichier .exe ou .dll.</span><span class="sxs-lookup"><span data-stu-id="661a7-134">Regardless of which **/langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="661a7-135">Les assemblys friend et [/moduleassemblyname (Option du compilateur C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), qui fonctionnent sous **/langversion:ISO-1**, représentent la seule exception.</span><span class="sxs-lookup"><span data-stu-id="661a7-135">One exception is friend assemblies and [/moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **/langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="661a7-136">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="661a7-136">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="661a7-137">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="661a7-137">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="661a7-138">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="661a7-138">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="661a7-139">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="661a7-139">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="661a7-140">Modifiez la propriété **Version du langage**.</span><span class="sxs-lookup"><span data-stu-id="661a7-140">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="661a7-141">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="661a7-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="661a7-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="661a7-142">See Also</span></span>  
 <span data-ttu-id="661a7-143">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="661a7-143">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="661a7-144">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="661a7-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)   
 
### <a name="c-language-specification"></a><span data-ttu-id="661a7-145">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="661a7-145">C# Language Specification</span></span>
 <span data-ttu-id="661a7-146">[Informations de référence sur la spécification du langage C#](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="661a7-146">[C# Language Specification Reference](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span></span>   
 <span data-ttu-id="661a7-147">C# 1.0/1.1 [ISO/IEC 23270 : 2003](https://www.iso.org/standard/36768.html) Technologies de l’information -- Spécification du langage C# : Catalogue ISO</span><span class="sxs-lookup"><span data-stu-id="661a7-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>   
 <span data-ttu-id="661a7-148">C# 2.0 [ISO/IEC 23270 : 2006](https://www.iso.org/standard/42926.html) Technologies de l’information -- Spécification du langage C# : Catalogue ISO</span><span class="sxs-lookup"><span data-stu-id="661a7-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>   
 <span data-ttu-id="661a7-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270:2006 au format PDF : Normes ISO disponibles gratuitement</span><span class="sxs-lookup"><span data-stu-id="661a7-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270:2006 in PDF format : ISO Freely Available Standards</span></span>   
 <span data-ttu-id="661a7-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) Spécification du langage C# version 3.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="661a7-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# Language Specification Version 3.0 : Microsoft Corporation</span></span>   
 <span data-ttu-id="661a7-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Norme ECMA-334 4e édition</span><span class="sxs-lookup"><span data-stu-id="661a7-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span></span>    
 <span data-ttu-id="661a7-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/en-us/download/details.aspx?id=7029) Spécification du langage C# version 5.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="661a7-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/en-us/download/details.aspx?id=7029) C# Language Specification Version 5.0 : Microsoft Corporation</span></span>   
 <span data-ttu-id="661a7-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) Spécification du langage C# version 6 - Ébauche non officielle : .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="661a7-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# Language Specification Version 6 - Unofficial Draft : .NET Foundation</span></span>   
 <span data-ttu-id="661a7-154">C# 7.0 (actuellement non disponible)</span><span class="sxs-lookup"><span data-stu-id="661a7-154">C# 7.0 (not currently available)</span></span>   

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)   
 C# 7.2 (spec is not yet finished)   
 C# 8.0 (spec is not yet finished)   
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="661a7-155">Version minimale obligatoire du compilateur pour une prise en charge de toutes les fonctionnalités du langage</span><span class="sxs-lookup"><span data-stu-id="661a7-155">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="661a7-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a> : Microsoft Visual Studio/Build Tools .Net 2002 ou compilateur .Net Framework 1.0 intégré</span><span class="sxs-lookup"><span data-stu-id="661a7-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="661a7-157">[↩](#TISO2)<a name="FISO2">ISO2</a> : Microsoft Visual Studio/Build Tools 2005 ou compilateur .Net Framework 2.0 intégré</span><span class="sxs-lookup"><span data-stu-id="661a7-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="661a7-158">[↩](#TCS3)<a name="FCS3">CS3</a> : Microsoft Visual Studio/Build Tools 2008 ou compilateur .Net Framework 3.5 intégré</span><span class="sxs-lookup"><span data-stu-id="661a7-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="661a7-159">[↩](#TCS4)<a name="FCS4">CS4</a> : Microsoft Visual Studio/Build Tools 2010 ou compilateur .Net Framework 4.0 intégré</span><span class="sxs-lookup"><span data-stu-id="661a7-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="661a7-160">[↩](#TCS5)<a name="FCS5">CS5</a> : Microsoft Visual Studio/Build Tools 2012 ou compilateur .Net Framework 4.5 intégré</span><span class="sxs-lookup"><span data-stu-id="661a7-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="661a7-161">[↩](#TCS6)<a name="FCS6">CS6</a> : Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="661a7-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="661a7-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a> : Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="661a7-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->

