---
title: /optionexplicit | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
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
ms.openlocfilehash: 3d2622c08b863233c8e1088bad252b37b3b38b04
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="optionexplicit"></a><span data-ttu-id="daa1c-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="daa1c-102">/optionexplicit</span></span>
<span data-ttu-id="daa1c-103">Indique au compilateur de signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="daa1c-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daa1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="daa1c-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="daa1c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="daa1c-105">Arguments</span></span>  
 <span data-ttu-id="daa1c-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="daa1c-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="daa1c-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="daa1c-107">Optional.</span></span> <span data-ttu-id="daa1c-108">Spécifiez `/optionexplicit+` pour requérir une déclaration explicite des variables.</span><span class="sxs-lookup"><span data-stu-id="daa1c-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="daa1c-109">Le `/optionexplicit+` option est la valeur par défaut et est identique à `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="daa1c-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="daa1c-110">La `/optionexplicit-` option permet une déclaration implicite des variables.</span><span class="sxs-lookup"><span data-stu-id="daa1c-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daa1c-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="daa1c-111">Remarks</span></span>  
 <span data-ttu-id="daa1c-112">Si le fichier de code source contient une [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l’instruction substitue le `/optionexplicit` du paramètre de compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="daa1c-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="daa1c-113">Pour définir /optionexplicit dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="daa1c-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="daa1c-114">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="daa1c-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="daa1c-115">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="daa1c-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="daa1c-116">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="daa1c-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="daa1c-117">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="daa1c-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="daa1c-118">Modifiez la valeur dans la **Option Explicit** boîte.</span><span class="sxs-lookup"><span data-stu-id="daa1c-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daa1c-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="daa1c-119">Example</span></span>  
 <span data-ttu-id="daa1c-120">Le code suivant compile si `/optionexplicit-` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="daa1c-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 <span data-ttu-id="daa1c-121">[!code-vb[VbVbalrCompiler n °&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="daa1c-121">[!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa1c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daa1c-122">See Also</span></span>  
 <span data-ttu-id="daa1c-123">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="daa1c-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="daa1c-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="daa1c-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="daa1c-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="daa1c-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="daa1c-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="daa1c-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="daa1c-127"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="daa1c-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="daa1c-128"> [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="daa1c-128"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="daa1c-129"> [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="daa1c-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
