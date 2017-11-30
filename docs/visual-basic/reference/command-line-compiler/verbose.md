---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a><span data-ttu-id="c5501-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="c5501-102">/verbose</span></span>
<span data-ttu-id="c5501-103">Indique au compilateur générer des messages d’état et d’erreur détaillés.</span><span class="sxs-lookup"><span data-stu-id="c5501-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5501-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5501-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5501-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c5501-105">Arguments</span></span>  
 <span data-ttu-id="c5501-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c5501-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c5501-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="c5501-107">Optional.</span></span> <span data-ttu-id="c5501-108">Spécification de `/verbose` est identique à la spécification `/verbose+`, ce qui entraîne le compilateur à émettre des messages détaillés.</span><span class="sxs-lookup"><span data-stu-id="c5501-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="c5501-109">La valeur par défaut de cette option est `/verbose-`.</span><span class="sxs-lookup"><span data-stu-id="c5501-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5501-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5501-110">Remarks</span></span>  
 <span data-ttu-id="c5501-111">Le `/verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys chargés par un module et affiche les fichiers qui sont en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="c5501-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5501-112">Le `/verbose` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c5501-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5501-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5501-113">Example</span></span>  
 <span data-ttu-id="c5501-114">Le code suivant compile `In.vb` et indique au compilateur d’afficher des informations d’état détaillées.</span><span class="sxs-lookup"><span data-stu-id="c5501-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5501-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5501-115">See Also</span></span>  
 [<span data-ttu-id="c5501-116">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5501-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c5501-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="c5501-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
