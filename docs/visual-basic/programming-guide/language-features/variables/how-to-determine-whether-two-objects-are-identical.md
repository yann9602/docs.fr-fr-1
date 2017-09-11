---
title: "Comment : déterminer si deux objets sont identiques (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
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
ms.openlocfilehash: c9621412eb1429ed07d8861114a67a67b6c1d58c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="65d17-102">Comment : déterminer si deux objets sont identiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65d17-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="65d17-103">Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], deux références de variable sont considérés comme identiques si leurs pointeurs sont les mêmes, autrement dit, si les deux variables pointent vers la même instance de classe en mémoire.</span><span class="sxs-lookup"><span data-stu-id="65d17-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="65d17-104">Par exemple, dans une application Windows Forms, vous souhaiterez effectuer une comparaison pour déterminer si l’instance actuelle (`Me`) est identique à une instance particulière, tel que `Form2`.</span><span class="sxs-lookup"><span data-stu-id="65d17-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="65d17-105">fournit deux opérateurs pour comparer des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="65d17-105"> provides two operators to compare pointers.</span></span> <span data-ttu-id="65d17-106">Le [est un opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) retourne `True` si les objets sont identiques et le [opérateur IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retourne `True` si elles ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="65d17-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="65d17-107">Comment déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="65d17-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="65d17-108">Pour déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="65d17-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="65d17-109">Configurer un `Boolean` expression pour tester les deux objets.</span><span class="sxs-lookup"><span data-stu-id="65d17-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="65d17-110">Dans votre expression de test, utilisez le `Is` opérateur avec les deux objets comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="65d17-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="65d17-111">`Is`Retourne `True` si les objets pointent vers la même instance de classe.</span><span class="sxs-lookup"><span data-stu-id="65d17-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="65d17-112">Déterminer si deux objets ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="65d17-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="65d17-113">Parfois, vous souhaitez exécuter une action si les deux objets ne sont pas identiques, et il peut être délicat de combiner `Not` et `Is`, par exemple `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="65d17-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="65d17-114">Dans ce cas, vous pouvez utiliser la `IsNot` opérateur.</span><span class="sxs-lookup"><span data-stu-id="65d17-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="65d17-115">Pour déterminer si deux objets ne sont pas identiques</span><span class="sxs-lookup"><span data-stu-id="65d17-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="65d17-116">Configurer un `Boolean` expression pour tester les deux objets.</span><span class="sxs-lookup"><span data-stu-id="65d17-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="65d17-117">Dans votre expression de test, utilisez le `IsNot` opérateur avec les deux objets comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="65d17-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="65d17-118">`IsNot`Retourne `True` si les objets ne pointent pas vers la même instance de classe.</span><span class="sxs-lookup"><span data-stu-id="65d17-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65d17-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="65d17-119">Example</span></span>  
 <span data-ttu-id="65d17-120">L’exemple suivant teste des paires de `Object` variables pour voir si elles pointent vers la même instance de classe.</span><span class="sxs-lookup"><span data-stu-id="65d17-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 <span data-ttu-id="65d17-121">[!code-vb[VbVbalrKeywords&#14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="65d17-121">[!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span></span>  
  
 <span data-ttu-id="65d17-122">L’exemple précédent affiche la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="65d17-122">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="65d17-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65d17-123">See Also</span></span>  
 <span data-ttu-id="65d17-124">[Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="65d17-124">[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="65d17-125"> [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="65d17-125"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="65d17-126"> [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="65d17-126"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="65d17-127"> [Opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="65d17-127"> [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="65d17-128"> [IsNot, opérateur](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="65d17-128"> [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="65d17-129"> [Comment : déterminer si deux objets sont liés.](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="65d17-129"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="65d17-130"> [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="65d17-130"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>
