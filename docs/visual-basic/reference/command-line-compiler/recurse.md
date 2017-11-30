---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a><span data-ttu-id="0bf59-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="0bf59-102">/recurse</span></span>
<span data-ttu-id="0bf59-103">Compile les fichiers de code source dans tous les répertoires enfants du répertoire spécifié ou le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="0bf59-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bf59-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bf59-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0bf59-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="0bf59-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0bf59-106">Optional.</span></span> <span data-ttu-id="0bf59-107">Répertoire dans lequel vous voulez commencer la recherche.</span><span class="sxs-lookup"><span data-stu-id="0bf59-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="0bf59-108">Si non spécifié, la recherche commence dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="0bf59-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="0bf59-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0bf59-109">Required.</span></span> <span data-ttu-id="0bf59-110">Le ou les fichiers à rechercher.</span><span class="sxs-lookup"><span data-stu-id="0bf59-110">The file(s) to search for.</span></span> <span data-ttu-id="0bf59-111">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="0bf59-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bf59-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="0bf59-112">Remarks</span></span>  
 <span data-ttu-id="0bf59-113">Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="0bf59-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="0bf59-114">Si aucun nom de fichier de sortie n’est spécifié, le compilateur base le nom de fichier de sortie sur le premier fichier d’entrée traité.</span><span class="sxs-lookup"><span data-stu-id="0bf59-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="0bf59-115">Il s’agit généralement du premier fichier dans la liste des fichiers compilés lorsqu’ils sont affichés par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="0bf59-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="0bf59-116">Pour cette raison, il est préférable de spécifier un fichier de sortie à l’aide de la `/out` option.</span><span class="sxs-lookup"><span data-stu-id="0bf59-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bf59-117">Le `/recurse` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0bf59-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf59-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="0bf59-118">Example</span></span>  
 <span data-ttu-id="0bf59-119">Le code suivant compile tous les [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fichiers dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0bf59-119">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="0bf59-120">Le code suivant compile tous les [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] les fichiers dans le `Test\ABC` répertoire et ses sous-répertoires, puis génère `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="0bf59-120">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bf59-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bf59-121">See Also</span></span>  
 [<span data-ttu-id="0bf59-122">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bf59-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0bf59-123">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bf59-123">/out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="0bf59-124">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="0bf59-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
