---
title: '#<a name="const-directive"></a>#Const (directive)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a><span data-ttu-id="baea1-102">#Const, directive</span><span class="sxs-lookup"><span data-stu-id="baea1-102">#Const Directive</span></span>
<span data-ttu-id="baea1-103">Définit des constantes conditionnelles du compilateur pour Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="baea1-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baea1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baea1-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="baea1-105">Composants</span><span class="sxs-lookup"><span data-stu-id="baea1-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="baea1-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="baea1-106">Required.</span></span> <span data-ttu-id="baea1-107">Nom de la constante définie.</span><span class="sxs-lookup"><span data-stu-id="baea1-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="baea1-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="baea1-108">Required.</span></span> <span data-ttu-id="baea1-109">Littéral, autre constante de compilation conditionnelle ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques à l’exception `Is`.</span><span class="sxs-lookup"><span data-stu-id="baea1-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baea1-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="baea1-110">Remarks</span></span>  
 <span data-ttu-id="baea1-111">Constantes de compilation conditionnelle sont toujours privées pour le fichier dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="baea1-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="baea1-112">Vous ne pouvez pas créer de constantes de compilation publiques à l’aide de la `#Const` directive ; vous pouvez les créer que dans l’interface utilisateur ou avec la `/define` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="baea1-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="baea1-113">Vous pouvez utiliser uniquement des constantes de compilation conditionnelle et des littéraux dans `expression`.</span><span class="sxs-lookup"><span data-stu-id="baea1-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="baea1-114">À l’aide d’une constante standard définie avec `Const` provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="baea1-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="baea1-115">À l’inverse, vous pouvez utiliser des constantes définies avec le `#Const` mot clé uniquement pour la compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="baea1-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="baea1-116">Les constantes peuvent également être non, auquel cas ils ont une valeur de `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="baea1-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baea1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="baea1-117">Example</span></span>  
 <span data-ttu-id="baea1-118">Cet exemple utilise la directive `#Const`.</span><span class="sxs-lookup"><span data-stu-id="baea1-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="baea1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baea1-119">See Also</span></span>  
 [<span data-ttu-id="baea1-120">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baea1-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="baea1-121">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="baea1-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="baea1-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="baea1-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="baea1-123">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="baea1-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="baea1-124">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="baea1-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
