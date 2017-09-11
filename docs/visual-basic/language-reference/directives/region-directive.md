---
title: "#La Directive région | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
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
ms.openlocfilehash: 86b8e9ce99a8c12e290f5efdc5a5c4da57f350d9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="region-directive"></a>#<span data-ttu-id="eef38-102">Directive de région</span><span class="sxs-lookup"><span data-stu-id="eef38-102">Region Directive</span></span>
<span data-ttu-id="eef38-103">Réduit et masque des sections de code dans des fichiers Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eef38-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eef38-104">Syntax</span></span>  
  
```  
  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="eef38-105">Composants</span><span class="sxs-lookup"><span data-stu-id="eef38-105">Parts</span></span>  
  
|<span data-ttu-id="eef38-106">Terme</span><span class="sxs-lookup"><span data-stu-id="eef38-106">Term</span></span>|<span data-ttu-id="eef38-107">Définition</span><span class="sxs-lookup"><span data-stu-id="eef38-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="eef38-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eef38-108">Required.</span></span> <span data-ttu-id="eef38-109">Chaîne qui joue le rôle du titre d'une région quand elle est réduite.</span><span class="sxs-lookup"><span data-stu-id="eef38-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="eef38-110">Les régions sont réduites par défaut.</span><span class="sxs-lookup"><span data-stu-id="eef38-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="eef38-111">Met fin au bloc `#Region`.</span><span class="sxs-lookup"><span data-stu-id="eef38-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eef38-112">Notes</span><span class="sxs-lookup"><span data-stu-id="eef38-112">Remarks</span></span>  
 <span data-ttu-id="eef38-113">Utilisez la directive `#Region` pour spécifier un bloc de code que vous pouvez développer ou réduire dans le mode Plan de l'éditeur de code Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eef38-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="eef38-114">Vous pouvez placer, ou *imbriquer*, régions dans d’autres régions pour grouper des régions semblables ensemble.</span><span class="sxs-lookup"><span data-stu-id="eef38-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eef38-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="eef38-115">Example</span></span>  
 <span data-ttu-id="eef38-116">Cet exemple utilise la directive `#Region`.</span><span class="sxs-lookup"><span data-stu-id="eef38-116">This example uses the `#Region` directive.</span></span>  
  
 <span data-ttu-id="eef38-117">[!code-vb[VbVbalrConditionalComp n °&4;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="eef38-117">[!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef38-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eef38-118">See Also</span></span>  
 <span data-ttu-id="eef38-119">[#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="eef38-119">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="eef38-120"> [Mode plan](https://docs.microsoft.com/visualstudio/ide/outlining) </span><span class="sxs-lookup"><span data-stu-id="eef38-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining) </span></span>  
<span data-ttu-id="eef38-121"> [Guide pratique : réduire et masquer des sections de code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span><span class="sxs-lookup"><span data-stu-id="eef38-121"> [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span></span>
