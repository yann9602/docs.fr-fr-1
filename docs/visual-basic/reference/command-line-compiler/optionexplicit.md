---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="a3b36-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="a3b36-102">/optionexplicit</span></span>
<span data-ttu-id="a3b36-103">Indique au compilateur de signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="a3b36-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3b36-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3b36-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a3b36-105">Arguments</span></span>  
 <span data-ttu-id="a3b36-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a3b36-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a3b36-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="a3b36-107">Optional.</span></span> <span data-ttu-id="a3b36-108">Spécifiez `/optionexplicit+` pour exiger la déclaration explicite des variables.</span><span class="sxs-lookup"><span data-stu-id="a3b36-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="a3b36-109">Le `/optionexplicit+` option est la valeur par défaut et est identique à `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="a3b36-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="a3b36-110">Le `/optionexplicit-` option permet une déclaration implicite des variables.</span><span class="sxs-lookup"><span data-stu-id="a3b36-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3b36-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="a3b36-111">Remarks</span></span>  
 <span data-ttu-id="a3b36-112">Si le fichier de code source contient un [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l’instruction substitue le `/optionexplicit` paramètre du compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a3b36-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="a3b36-113">Pour définir /optionexplicit dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a3b36-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="a3b36-114">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="a3b36-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a3b36-115">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a3b36-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="a3b36-116">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="a3b36-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="a3b36-117">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="a3b36-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="a3b36-118">Modifiez la valeur dans la **Option Explicit** boîte.</span><span class="sxs-lookup"><span data-stu-id="a3b36-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3b36-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3b36-119">Example</span></span>  
 <span data-ttu-id="a3b36-120">Le code suivant compile si `/optionexplicit-` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a3b36-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a3b36-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3b36-121">See Also</span></span>  
 [<span data-ttu-id="a3b36-122">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3b36-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a3b36-123">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="a3b36-123">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="a3b36-124">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="a3b36-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="a3b36-125">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="a3b36-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="a3b36-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="a3b36-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="a3b36-127">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3b36-127">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="a3b36-128">Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="a3b36-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
