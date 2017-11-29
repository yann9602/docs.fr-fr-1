---
title: '#<a name="ifthenelse-directives"></a>If... Then... #Else, Directives'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="8afb3-102">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="8afb3-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="8afb3-103">Compilation conditionnelle des blocs de code Visual Basic sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="8afb3-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afb3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8afb3-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="8afb3-105">Composants</span><span class="sxs-lookup"><span data-stu-id="8afb3-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="8afb3-106">Requis pour `#If` et `#ElseIf` instructions, facultatif ailleurs.</span><span class="sxs-lookup"><span data-stu-id="8afb3-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="8afb3-107">Toute expression, exclusivement consistant en une ou plusieurs constantes de compilation conditionnelle, les littéraux et les opérateurs, qui prend la valeur `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="8afb3-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="8afb3-108">Requis pour `#If` bloc d’instructions, facultatif ailleurs.</span><span class="sxs-lookup"><span data-stu-id="8afb3-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="8afb3-109">Lignes de programme Visual Basic ou des directives de compilateur qui sont compilés si l’expression associée a la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="8afb3-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="8afb3-110">Met fin à la `#If` bloc d’instructions.</span><span class="sxs-lookup"><span data-stu-id="8afb3-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8afb3-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="8afb3-111">Remarks</span></span>  
 <span data-ttu-id="8afb3-112">Sur la surface, le comportement de la `#If...Then...#Else` directives semble être le même que celui de la `If...Then...Else` instructions.</span><span class="sxs-lookup"><span data-stu-id="8afb3-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="8afb3-113">Toutefois, le `#If...Then...#Else` directives évaluent ce qui est compilé par le compilateur, alors que le `If...Then...Else` instructions évaluent les conditions au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8afb3-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="8afb3-114">Compilation conditionnelle est généralement utilisée pour compiler le même programme pour les différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="8afb3-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="8afb3-115">Il est également utilisé pour empêcher le code d’apparaître dans un fichier exécutable de débogage.</span><span class="sxs-lookup"><span data-stu-id="8afb3-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="8afb3-116">Code exclu lors de la compilation conditionnelle est totalement absent du fichier exécutable final, afin qu’il n’a aucun effet sur la taille ou des performances.</span><span class="sxs-lookup"><span data-stu-id="8afb3-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="8afb3-117">Quel que soit le résultat des évaluations, toutes les expressions sont évaluées à l’aide de `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="8afb3-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="8afb3-118">Le `Option Compare` instruction n’affecte pas les expressions dans `#If` et `#ElseIf` instructions.</span><span class="sxs-lookup"><span data-stu-id="8afb3-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afb3-119">Aucune forme d’une ligne de la `#If`, `#Else`, `#ElseIf`, et `#End If` directives existe.</span><span class="sxs-lookup"><span data-stu-id="8afb3-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="8afb3-120">Aucun autre code ne peut apparaître sur la même ligne qu’une des directives.</span><span class="sxs-lookup"><span data-stu-id="8afb3-120">No other code can appear on the same line as any of the directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8afb3-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="8afb3-121">Example</span></span>  
 <span data-ttu-id="8afb3-122">Cet exemple utilise le `#If...Then...#Else` construction pour déterminer s’il faut compiler certaines instructions.</span><span class="sxs-lookup"><span data-stu-id="8afb3-122">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8afb3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8afb3-123">See Also</span></span>  
 [<span data-ttu-id="8afb3-124">#Const (directive)</span><span class="sxs-lookup"><span data-stu-id="8afb3-124">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="8afb3-125">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="8afb3-125">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="8afb3-126">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="8afb3-126">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
