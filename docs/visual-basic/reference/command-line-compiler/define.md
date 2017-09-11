---
title: /define (Visual Basic) | Documents Microsoft
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
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
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
ms.openlocfilehash: e4eac32b4ab7259b9d3fd2ec37e21406c4cec326
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="define-visual-basic"></a><span data-ttu-id="76e56-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76e56-102">/define (Visual Basic)</span></span>
<span data-ttu-id="76e56-103">Définit des constantes conditionnelles du compilateur.</span><span class="sxs-lookup"><span data-stu-id="76e56-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76e56-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="76e56-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="76e56-105">Arguments</span></span>  
  
|<span data-ttu-id="76e56-106">Terme</span><span class="sxs-lookup"><span data-stu-id="76e56-106">Term</span></span>|<span data-ttu-id="76e56-107">Définition</span><span class="sxs-lookup"><span data-stu-id="76e56-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="76e56-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="76e56-108">Required.</span></span> <span data-ttu-id="76e56-109">Symbole à définir.</span><span class="sxs-lookup"><span data-stu-id="76e56-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="76e56-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="76e56-110">Optional.</span></span> <span data-ttu-id="76e56-111">Valeur à affecter au `symbol`.</span><span class="sxs-lookup"><span data-stu-id="76e56-111">The value to assign `symbol`.</span></span> <span data-ttu-id="76e56-112">Si `value` est une chaîne, elle doit être entourée par des séquences de barre oblique inverse/guillemets (\\») au lieu de guillemets.</span><span class="sxs-lookup"><span data-stu-id="76e56-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="76e56-113">Si aucune valeur n'est spécifiée, il prend la valeur True.</span><span class="sxs-lookup"><span data-stu-id="76e56-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76e56-114">Notes</span><span class="sxs-lookup"><span data-stu-id="76e56-114">Remarks</span></span>  
 <span data-ttu-id="76e56-115">Le `/define` option a un effet semblable à l’aide un `#Const` directive de préprocesseur dans votre fichier source, excepté que les constantes définies avec `/define` sont publiques et s’appliquent à tous les fichiers dans le projet.</span><span class="sxs-lookup"><span data-stu-id="76e56-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="76e56-116">Vous pouvez utiliser les symboles créés par cette option avec la directive `#If`...`Then`...`#Else` pour effectuer une compilation conditionnelle des fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="76e56-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="76e56-117">`/d` est la forme abrégée de `/define`.</span><span class="sxs-lookup"><span data-stu-id="76e56-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="76e56-118">Vous pouvez définir plusieurs symboles avec `/define` en utilisant une virgule pour séparer les définitions de symbole.</span><span class="sxs-lookup"><span data-stu-id="76e56-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="76e56-119">Pour définir /define dans l'environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76e56-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="76e56-120">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="76e56-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="76e56-121">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="76e56-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="76e56-122">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="76e56-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="76e56-123">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="76e56-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="76e56-124">3.  Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="76e56-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="76e56-125">4.  Modifiez la valeur dans la **constantes personnalisées** boîte.</span><span class="sxs-lookup"><span data-stu-id="76e56-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76e56-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="76e56-126">Example</span></span>  
 <span data-ttu-id="76e56-127">Le code suivant définit deux constantes de compilation conditionnelle, puis les utilise.</span><span class="sxs-lookup"><span data-stu-id="76e56-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 <span data-ttu-id="76e56-128">[!code-vb[VbVbalrCompiler n °&45;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="76e56-128">[!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e56-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76e56-129">See Also</span></span>  
 <span data-ttu-id="76e56-130">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="76e56-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="76e56-131"> [#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="76e56-131"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="76e56-132"> [#Const, Directive](../../../visual-basic/language-reference/directives/const-directive.md) </span><span class="sxs-lookup"><span data-stu-id="76e56-132"> [#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) </span></span>  
<span data-ttu-id="76e56-133"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="76e56-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
