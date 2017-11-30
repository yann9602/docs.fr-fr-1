---
title: "Comment : réduire et masquer des sections de code (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a31f0c8af9b84e87ebe1e5191d72d19be8340f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="c96a3-102">Comment : réduire et masquer des sections de code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c96a3-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="c96a3-103">Le `#Region` directive vous permet de réduire et masquer des sections de code dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fichiers.</span><span class="sxs-lookup"><span data-stu-id="c96a3-103">The `#Region` directive enables you to collapse and hide sections of code in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files.</span></span> <span data-ttu-id="c96a3-104">Le `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez la [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="c96a3-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] code editor.</span></span> <span data-ttu-id="c96a3-105">La possibilité de masquer le code de manière sélective rend vos fichiers plus gérable et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="c96a3-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="c96a3-106">Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="c96a3-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="c96a3-107">`#Region`directives prennent en charge une sémantique de bloc de code comme `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="c96a3-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="c96a3-108">Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer par une autre ; le début et fin doivent être dans le même bloc.</span><span class="sxs-lookup"><span data-stu-id="c96a3-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="c96a3-109">`#Region`directives ne sont pas pris en charge dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="c96a3-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="c96a3-110">Pour réduire et masquer une section de code</span><span class="sxs-lookup"><span data-stu-id="c96a3-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="c96a3-111">Placez la section de code entre les `#Region` et `#End Region` instructions, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c96a3-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="c96a3-112">Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code ; par conséquent, les utilisateurs peuvent définir leurs propres blocs de procédures et des classes qui peuvent, à son tour, être réduits.</span><span class="sxs-lookup"><span data-stu-id="c96a3-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="c96a3-113">`#Region`les blocs peuvent également être imbriqués dans d’autres `#Region` blocs.</span><span class="sxs-lookup"><span data-stu-id="c96a3-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c96a3-114">Masquage du code n’empêche pas sa compilation et n’affecte pas `#If...#End If` instructions.</span><span class="sxs-lookup"><span data-stu-id="c96a3-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96a3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c96a3-115">See Also</span></span>  
 [<span data-ttu-id="c96a3-116">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="c96a3-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="c96a3-117">#Region (directive)</span><span class="sxs-lookup"><span data-stu-id="c96a3-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="c96a3-118">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="c96a3-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="c96a3-119">Mode Plan</span><span class="sxs-lookup"><span data-stu-id="c96a3-119">Outlining</span></span>](/visualstudio/ide/outlining)
