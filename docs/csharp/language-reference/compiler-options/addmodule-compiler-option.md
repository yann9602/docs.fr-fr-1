---
title: "-addmodule (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2652102682de9dff24c66180dde36f33b4b6bbfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule-c-compiler-options"></a><span data-ttu-id="9bbcb-102">/addmodule (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9bbcb-102">/addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="9bbcb-103">Cette option ajoute un module créé avec le commutateur target:module à la compilation actuelle.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bbcb-104">Syntax</span></span>  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9bbcb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9bbcb-105">Arguments</span></span>  
 <span data-ttu-id="9bbcb-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="9bbcb-106">`file`, `file2`</span></span>  
 <span data-ttu-id="9bbcb-107">Fichier de sortie qui contient des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-107">An output file that contains metadata.</span></span> <span data-ttu-id="9bbcb-108">Le fichier ne peut pas contenir un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="9bbcb-109">Pour importer plusieurs fichiers, séparez les noms des fichiers par une virgule ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bbcb-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="9bbcb-110">Remarks</span></span>  
 <span data-ttu-id="9bbcb-111">Tous les modules ajoutés par **/addmodule** doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-111">All modules added with **/addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="9bbcb-112">Vous pouvez donc spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="9bbcb-113">Si le module n’est pas dans le répertoire de l’application au moment de l’exécution, vous obtiendrez <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="9bbcb-114">`file` ne peut pas contenir un assembly.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="9bbcb-115">Si, par exemple, le fichier de sortie a été créé avec [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), ses métadonnées peuvent être importées avec **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-115">For example, if the output file was created with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **/addmodule**.</span></span>  
  
 <span data-ttu-id="9bbcb-116">Si le fichier de sortie a été créé avec une option **/target** autre que **/target:module**, ses métadonnées ne peuvent pas être importées avec **/addmodule**, mais peuvent l’être avec [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9bbcb-116">If the output file was created with a **/target** option other than **/target:module**, its metadata cannot be imported with **/addmodule** but can be imported with [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="9bbcb-117">Cette option du compilateur n’est pas disponible dans Visual Studio ; un projet ne peut pas référencer un module.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="9bbcb-118">Par ailleurs, cette option du compilateur ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="9bbcb-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbcb-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9bbcb-119">Example</span></span>  
 <span data-ttu-id="9bbcb-120">Compilez le fichier source `input.cs` et ajoutez les métadonnées de `metad1.netmodule` et `metad2.netmodule` pour produire `out.exe` :</span><span class="sxs-lookup"><span data-stu-id="9bbcb-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bbcb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bbcb-121">See Also</span></span>  
 [<span data-ttu-id="9bbcb-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="9bbcb-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="9bbcb-123">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="9bbcb-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="9bbcb-124">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="9bbcb-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="9bbcb-125">Guide pratique pour générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="9bbcb-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
