---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a><span data-ttu-id="d2872-102">/utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2872-102">/utf8output (Visual Basic)</span></span>
<span data-ttu-id="d2872-103">Affiche les résultats de la compilation au format d'encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d2872-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2872-104">Syntax</span></span>  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2872-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2872-105">Arguments</span></span>  
 <span data-ttu-id="d2872-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d2872-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d2872-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="d2872-107">Optional.</span></span> <span data-ttu-id="d2872-108">La valeur par défaut de cette option est `/utf8output-`, ce qui signifie que la sortie du compilateur n’utilise pas le codage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d2872-108">The default for this option is `/utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="d2872-109">Spécification de `/utf8output` est identique à la spécification `/utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="d2872-109">Specifying `/utf8output` is the same as specifying `/utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2872-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2872-110">Remarks</span></span>  
 <span data-ttu-id="d2872-111">Dans certaines configurations internationales, sortie du compilateur ne peut pas être affiché correctement dans la console.</span><span class="sxs-lookup"><span data-stu-id="d2872-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="d2872-112">Dans ce cas, utilisez `/utf8output` et rediriger la sortie du compilateur vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="d2872-112">In such situations, use `/utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2872-113">Le `/utf8output` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d2872-113">The `/utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2872-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2872-114">Example</span></span>  
 <span data-ttu-id="d2872-115">Le code suivant compile `In.vb` et indique au compilateur d’afficher de sortie à l’aide du codage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d2872-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2872-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2872-116">See Also</span></span>  
 [<span data-ttu-id="d2872-117">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2872-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d2872-118">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="d2872-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
