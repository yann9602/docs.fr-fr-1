---
title: /addmodule | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2db0db5b5dd94f03e67d8680624e2a4ad23587f7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="addmodule"></a><span data-ttu-id="0238a-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="0238a-102">/addmodule</span></span>
<span data-ttu-id="0238a-103">Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="0238a-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0238a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0238a-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0238a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0238a-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="0238a-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0238a-106">Required.</span></span> <span data-ttu-id="0238a-107">Liste délimitée par des virgules des fichiers qui contiennent des métadonnées, mais ne contiennent pas de manifestes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0238a-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="0238a-108">Les noms de fichier contenant des espaces doivent être entourés de guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="0238a-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0238a-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="0238a-109">Remarks</span></span>  
 <span data-ttu-id="0238a-110">Les fichiers répertoriés par le `fileList` paramètre doit être créé avec la `/target:module` option, ou avec l’équivalent d’un autre compilateur `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="0238a-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="0238a-111">Tous les modules ajoutés avec `/addmodule` doit être dans le même répertoire que le fichier de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0238a-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="0238a-112">Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit être dans le répertoire de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0238a-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="0238a-113">Si elle n’est pas le cas, vous obtenez un <xref:System.TypeLoadException>erreur.</xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="0238a-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="0238a-114">Si vous spécifiez (implicitement ou explicitement) n’importe quel[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option autre que `/target:module` avec `/addmodule`, les fichiers que vous transmettez à `/addmodule` font partie de l’assembly du projet.</span><span class="sxs-lookup"><span data-stu-id="0238a-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="0238a-115">Un assembly est requis pour exécuter un fichier de sortie qui contient un ou plusieurs fichiers ajoutés avec `/addmodule`.</span><span class="sxs-lookup"><span data-stu-id="0238a-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="0238a-116">Utilisez [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pour importer des métadonnées à partir d’un fichier qui contient un assembly.</span><span class="sxs-lookup"><span data-stu-id="0238a-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0238a-117">La `/addmodule` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0238a-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0238a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="0238a-118">Example</span></span>  
 <span data-ttu-id="0238a-119">Le code suivant crée un module.</span><span class="sxs-lookup"><span data-stu-id="0238a-119">The following code creates a module.</span></span>  
  
 <span data-ttu-id="0238a-120">[!code-vb[VbVbalrCompiler&#47;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0238a-120">[!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span></span>  
  
 <span data-ttu-id="0238a-121">Le code suivant importe les types du module.</span><span class="sxs-lookup"><span data-stu-id="0238a-121">The following code imports the module's types.</span></span>  
  
 <span data-ttu-id="0238a-122">[!code-vb[VbVbalrCompiler&#48;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0238a-122">[!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span></span>  
  
 <span data-ttu-id="0238a-123">Lorsque vous exécutez `t1`, il renvoie `802`.</span><span class="sxs-lookup"><span data-stu-id="0238a-123">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0238a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0238a-124">See Also</span></span>  
 <span data-ttu-id="0238a-125">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0238a-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0238a-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="0238a-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="0238a-127"> [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="0238a-127"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="0238a-128"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="0238a-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
