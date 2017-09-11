---
title: /recurse | Documents Microsoft
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
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
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
ms.openlocfilehash: 9ceb2f3bc9e4d0f1088258f504b7a49c58a29e35
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="recurse"></a><span data-ttu-id="7da1e-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="7da1e-102">/recurse</span></span>
<span data-ttu-id="7da1e-103">Compile les fichiers de code source dans tous les répertoires enfants du répertoire spécifié ou le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="7da1e-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7da1e-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="7da1e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7da1e-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="7da1e-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7da1e-106">Optional.</span></span> <span data-ttu-id="7da1e-107">Le répertoire dans lequel vous souhaitez commencer la recherche.</span><span class="sxs-lookup"><span data-stu-id="7da1e-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="7da1e-108">Si non spécifié, la recherche commence dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="7da1e-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="7da1e-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7da1e-109">Required.</span></span> <span data-ttu-id="7da1e-110">L’ou les fichiers à rechercher.</span><span class="sxs-lookup"><span data-stu-id="7da1e-110">The file(s) to search for.</span></span> <span data-ttu-id="7da1e-111">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7da1e-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7da1e-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="7da1e-112">Remarks</span></span>  
 <span data-ttu-id="7da1e-113">Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="7da1e-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="7da1e-114">Si aucun nom de fichier de sortie n’est spécifié, le compilateur base le nom de fichier de sortie sur le premier fichier d’entrée traité.</span><span class="sxs-lookup"><span data-stu-id="7da1e-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="7da1e-115">Il s’agit généralement du premier fichier dans la liste des fichiers compilés lorsqu’ils sont affichés par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="7da1e-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="7da1e-116">Pour cette raison, il est préférable de spécifier un fichier de sortie à l’aide de la `/out` option.</span><span class="sxs-lookup"><span data-stu-id="7da1e-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7da1e-117">La `/recurse` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7da1e-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7da1e-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="7da1e-118">Example</span></span>  
 <span data-ttu-id="7da1e-119">Le code suivant compile tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="7da1e-119">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="7da1e-120">Le code suivant compile tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de fichiers dans le `Test\ABC` répertoire et ses sous-répertoires, puis génère `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="7da1e-120">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7da1e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7da1e-121">See Also</span></span>  
 <span data-ttu-id="7da1e-122">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="7da1e-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="7da1e-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span><span class="sxs-lookup"><span data-stu-id="7da1e-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span></span>  
<span data-ttu-id="7da1e-124"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="7da1e-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
