---
title: "Comment : étiqueter des instructions (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="cad6c-102">Comment : étiqueter des instructions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cad6c-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="cad6c-103">Blocs d’instructions sont composés de lignes de code délimitées par le signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="cad6c-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="cad6c-104">Lignes de code, précédé d’une chaîne ou entier identifiant sont dites *intitulé*.</span><span class="sxs-lookup"><span data-stu-id="cad6c-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="cad6c-105">Les étiquettes d’instruction sont utilisées pour marquer une ligne de code pour identifier pour une utilisation avec des instructions telles que `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="cad6c-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="cad6c-106">Les étiquettes peuvent être soit des identificateurs Visual Basic valides, telles que celles qui identifient les éléments de programmation, soit des littéraux entiers.</span><span class="sxs-lookup"><span data-stu-id="cad6c-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="cad6c-107">Une étiquette doit apparaître au début d’une ligne de code source et doit être suivie par un signe deux-points, indépendamment de si elle est suivie par une instruction sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="cad6c-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="cad6c-108">Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à n’importe quel identificateur déjà défini.</span><span class="sxs-lookup"><span data-stu-id="cad6c-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="cad6c-109">Si elle n’est pas le cas, le compilateur suppose qu’il existe une étiquette.</span><span class="sxs-lookup"><span data-stu-id="cad6c-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="cad6c-110">Les étiquettes ont leur propre espace de déclaration et n’interfèrent pas avec d’autres identificateurs.</span><span class="sxs-lookup"><span data-stu-id="cad6c-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="cad6c-111">Portée d’une étiquette est le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="cad6c-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="cad6c-112">Déclaration d’étiquette est prioritaire en cas d’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="cad6c-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cad6c-113">Étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l’intérieur de méthodes.</span><span class="sxs-lookup"><span data-stu-id="cad6c-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="cad6c-114">Pour étiqueter une ligne de code</span><span class="sxs-lookup"><span data-stu-id="cad6c-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="cad6c-115">Placez un identificateur, suivi d’un signe deux-points, au début de la ligne de code source.</span><span class="sxs-lookup"><span data-stu-id="cad6c-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="cad6c-116">Par exemple, les lignes de code suivantes sont étiquetés avec `Jump` et `120`, respectivement :</span><span class="sxs-lookup"><span data-stu-id="cad6c-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cad6c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cad6c-117">See Also</span></span>  
 [<span data-ttu-id="cad6c-118">Instructions</span><span class="sxs-lookup"><span data-stu-id="cad6c-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="cad6c-119">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="cad6c-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="cad6c-120">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="cad6c-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
