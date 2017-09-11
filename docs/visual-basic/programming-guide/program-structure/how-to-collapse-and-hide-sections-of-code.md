---
title: "Comment : réduire et masquer des Sections de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
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
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
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
ms.openlocfilehash: 4dcd5cd5d79629fd008534112cb72d5bcfec476e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="72318-102">Comment : réduire et masquer des sections de code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72318-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="72318-103">Le `#Region` directive vous permet de réduire et masquer des sections de code dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fichiers.</span><span class="sxs-lookup"><span data-stu-id="72318-103">The `#Region` directive enables you to collapse and hide sections of code in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files.</span></span> <span data-ttu-id="72318-104">Le `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="72318-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] code editor.</span></span> <span data-ttu-id="72318-105">La possibilité de masquer le code de manière sélective rend vos fichiers plus gérable et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="72318-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="72318-106">Pour plus d’informations, voir [Mode Plan](https://docs.microsoft.com/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="72318-106">For more information, see [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="72318-107">`#Region`directives prennent en charge les sémantiques de bloc de code comme `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="72318-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="72318-108">Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer par une autre ; le début et fin doivent être dans le même bloc.</span><span class="sxs-lookup"><span data-stu-id="72318-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="72318-109">`#Region`directives ne sont pas pris en charge dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="72318-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="72318-110">Pour réduire et masquer une section de code</span><span class="sxs-lookup"><span data-stu-id="72318-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="72318-111">Placez la section de code entre les `#Region` et `#End Region` instructions, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="72318-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     <span data-ttu-id="72318-112">[!code-vb[VbVbalrConditionalComp n °&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="72318-112">[!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span></span>  
  
     <span data-ttu-id="72318-113">Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code ; par conséquent, les utilisateurs peuvent définir leurs propres blocs de procédures et des classes qui peuvent, à son tour, être réduits.</span><span class="sxs-lookup"><span data-stu-id="72318-113">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="72318-114">`#Region`les blocs peuvent également être imbriqués dans les autres `#Region` blocs.</span><span class="sxs-lookup"><span data-stu-id="72318-114">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="72318-115">Masquage du code n’empêche pas sa compilation et n’affecte pas `#If...#End If` instructions.</span><span class="sxs-lookup"><span data-stu-id="72318-115">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72318-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72318-116">See Also</span></span>  
 <span data-ttu-id="72318-117">[Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="72318-117">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<span data-ttu-id="72318-118"> [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="72318-118"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="72318-119"> [#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="72318-119"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="72318-120"> [Mode Plan](https://docs.microsoft.com/visualstudio/ide/outlining)</span><span class="sxs-lookup"><span data-stu-id="72318-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining)</span></span>
