---
title: /vbruntime | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cb07ed8c2f6070079cc51c290ff5a61305c5a5d3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="vbruntime"></a><span data-ttu-id="c1b06-102">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="c1b06-102">/vbruntime</span></span>
<span data-ttu-id="c1b06-103">Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.</span><span class="sxs-lookup"><span data-stu-id="c1b06-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1b06-104">Syntax</span></span>  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1b06-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c1b06-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="c1b06-106">Compiler sans référence à la bibliothèque Runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b06-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="c1b06-107">Compiler avec une référence à la bibliothèque Visual Basic Runtime par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1b06-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="c1b06-108">Compiler sans référence à la bibliothèque Visual Basic Runtime et incorporer la fonctionnalité principale de la bibliothèque Runtime Visual Basic dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c1b06-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="c1b06-109">Compiler avec une référence à la bibliothèque spécifiée (DLL).</span><span class="sxs-lookup"><span data-stu-id="c1b06-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1b06-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="c1b06-110">Remarks</span></span>  
 <span data-ttu-id="c1b06-111">La `/vbruntime` option du compilateur vous permet de spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b06-111">The `/vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="c1b06-112">Si vous compilez sans référence à la bibliothèque d’exécution Visual Basic, erreurs ou avertissements sont enregistrés sur les constructions de code ou de langage qui génèrent un appel à une application d’assistance du runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b06-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="c1b06-113">(A *du composant d’exécution Visual Basic* est une fonction définie dans Microsoft.VisualBasic.dll, qui est appelée lors de l’exécution pour exécuter une syntaxe de langue spécifique.)</span><span class="sxs-lookup"><span data-stu-id="c1b06-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="c1b06-114">Le `/vbruntime+` option produit le même comportement se produit si aucun `/vbruntime` le commutateur.</span><span class="sxs-lookup"><span data-stu-id="c1b06-114">The `/vbruntime+` option produces the same behavior that occurs if no `/vbruntime` switch is specified.</span></span> <span data-ttu-id="c1b06-115">Vous pouvez utiliser la `/vbruntime+` option permettant de remplacer la précédente `/vbruntime` commutateurs.</span><span class="sxs-lookup"><span data-stu-id="c1b06-115">You can use the `/vbruntime+` option to override previous `/vbruntime` switches.</span></span>  
  
 <span data-ttu-id="c1b06-116">La plupart des objets de la `My` type ne sont pas disponibles lorsque vous utilisez la `/vbruntime-` ou `vbruntime:``path` options.</span><span class="sxs-lookup"><span data-stu-id="c1b06-116">Most objects of the `My` type are unavailable when you use the `/vbruntime-` or `vbruntime:``path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="c1b06-117">L’incorporation de fonctionnalités principales Runtime de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1b06-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="c1b06-118">La `/vbruntime*` option vous permet de compiler sans référence à une bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="c1b06-118">The `/vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="c1b06-119">Au lieu de cela, les fonctionnalités principales de la bibliothèque Runtime Visual Basic sont incorporées dans l’assembly de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c1b06-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="c1b06-120">Vous pouvez utiliser cette option si votre application s’exécute sur des plateformes qui ne contiennent pas le runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b06-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="c1b06-121">Les membres du runtime suivants sont incorporés :</span><span class="sxs-lookup"><span data-stu-id="c1b06-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="c1b06-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions>(classe)</xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="c1b06-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="c1b06-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>(méthode)</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="c1b06-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="c1b06-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>(méthode)</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="c1b06-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="c1b06-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>(méthode)</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="c1b06-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="c1b06-126"><xref:Microsoft.VisualBasic.Constants.vbBack>(constante)</xref:Microsoft.VisualBasic.Constants.vbBack></span><span class="sxs-lookup"><span data-stu-id="c1b06-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="c1b06-127"><xref:Microsoft.VisualBasic.Constants.vbCr>(constante)</xref:Microsoft.VisualBasic.Constants.vbCr></span><span class="sxs-lookup"><span data-stu-id="c1b06-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="c1b06-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>(constante)</xref:Microsoft.VisualBasic.Constants.vbCrLf></span><span class="sxs-lookup"><span data-stu-id="c1b06-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="c1b06-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>(constante)</xref:Microsoft.VisualBasic.Constants.vbFormFeed></span><span class="sxs-lookup"><span data-stu-id="c1b06-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="c1b06-130"><xref:Microsoft.VisualBasic.Constants.vbLf>(constante)</xref:Microsoft.VisualBasic.Constants.vbLf></span><span class="sxs-lookup"><span data-stu-id="c1b06-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="c1b06-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>(constante)</xref:Microsoft.VisualBasic.Constants.vbNewLine></span><span class="sxs-lookup"><span data-stu-id="c1b06-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="c1b06-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>(constante)</xref:Microsoft.VisualBasic.Constants.vbNullChar></span><span class="sxs-lookup"><span data-stu-id="c1b06-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="c1b06-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>(constante)</xref:Microsoft.VisualBasic.Constants.vbNullString></span><span class="sxs-lookup"><span data-stu-id="c1b06-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="c1b06-134"><xref:Microsoft.VisualBasic.Constants.vbTab>(constante)</xref:Microsoft.VisualBasic.Constants.vbTab></span><span class="sxs-lookup"><span data-stu-id="c1b06-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="c1b06-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>(constante)</xref:Microsoft.VisualBasic.Constants.vbVerticalTab></span><span class="sxs-lookup"><span data-stu-id="c1b06-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="c1b06-136">Certains objets de la `My` type</span><span class="sxs-lookup"><span data-stu-id="c1b06-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="c1b06-137">Si vous compilez à l’aide de la `/vbruntime*` option et votre code fait référence à un membre de la bibliothèque Runtime Visual Basic qui n’est pas incorporé avec la fonctionnalité principale, le compilateur renvoie une erreur indiquant que le membre n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="c1b06-137">If you compile using the `/vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="c1b06-138">Référencement d’une bibliothèque spécifiée</span><span class="sxs-lookup"><span data-stu-id="c1b06-138">Referencing a specified library</span></span>  
 <span data-ttu-id="c1b06-139">Vous pouvez utiliser la `path` argument pour compiler avec une référence à une bibliothèque runtime personnalisée au lieu de la bibliothèque Visual Basic Runtime par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1b06-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="c1b06-140">Si la valeur de la `path` argument est un chemin d’accès complet à une DLL, le compilateur utilisera ce fichier comme bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="c1b06-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="c1b06-141">Si la valeur de la `path` argument n’est pas un chemin d’accès complet à une DLL, le compilateur Visual Basic recherchera la DLL identifiée dans le dossier actif tout d’abord.</span><span class="sxs-lookup"><span data-stu-id="c1b06-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="c1b06-142">Il recherche ensuite dans le chemin d’accès que vous avez spécifié à l’aide de la [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="c1b06-142">It will then search in the path that you have specified by using the [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="c1b06-143">Si le `/sdkpath` option du compilateur n’est pas utilisée, le compilateur recherchera la DLL identifiée dans le dossier .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="c1b06-143">If the `/sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b06-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1b06-144">Example</span></span>  
 <span data-ttu-id="c1b06-145">L’exemple suivant montre comment utiliser la `/vbruntime` option pour compiler avec une référence à une bibliothèque personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c1b06-145">The following example shows how to use the `/vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1b06-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1b06-146">See Also</span></span>  
 <span data-ttu-id="c1b06-147">[Base de Visual Basic – nouveau mode de compilation dans Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span><span class="sxs-lookup"><span data-stu-id="c1b06-147">[Visual Basic Core – New compilation mode in Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span></span>  
<span data-ttu-id="c1b06-148"> [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1b06-148"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="c1b06-149"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="c1b06-149"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="c1b06-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="c1b06-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
