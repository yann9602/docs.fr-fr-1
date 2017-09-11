---
title: "Détermination du Type Object (Visual Basic) | Documents Microsoft"
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
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
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
ms.openlocfilehash: fec7a275029dde469425b651d5b1220cb21ddbf6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="0b336-102">Détermination du type Object (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b336-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="0b336-103">Les variables objets génériques (autrement dit, les variables que vous déclarez comme `Object`) peuvent contenir les objets à partir de n’importe quelle classe.</span><span class="sxs-lookup"><span data-stu-id="0b336-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="0b336-104">Lorsque vous utilisez des variables de type `Object`, vous devrez peut-être prendre des mesures différentes selon la classe de l’objet ; par exemple, certains objets ne peuvent pas en charge une propriété ou méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="0b336-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0b336-105">offre deux moyens de déterminer quel type d’objet est stocké dans une variable objet : le `TypeName` (fonction) et `TypeOf...Is` (opérateur).</span><span class="sxs-lookup"><span data-stu-id="0b336-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="0b336-106">TypeName et TypeOf... Est</span><span class="sxs-lookup"><span data-stu-id="0b336-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="0b336-107">Le `TypeName` fonction retourne une chaîne et est le meilleur choix lorsque vous devez stocker ou afficher le nom de classe d’un objet, comme illustré dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="0b336-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="0b336-108">[!code-vb[VbVbalrOOP&#92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b336-108">[!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span></span>  
  
 <span data-ttu-id="0b336-109">Le `TypeOf...Is` opérateur est le meilleur choix pour tester le type d’un objet, car il est beaucoup plus rapide qu’une comparaison de chaîne équivalente à l’aide de `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="0b336-109">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="0b336-110">Le fragment de code suivant utilise `TypeOf...Is` dans un `If...Then...Else` instruction :</span><span class="sxs-lookup"><span data-stu-id="0b336-110">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 <span data-ttu-id="0b336-111">[!code-vb[VbVbalrOOP&#93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b336-111">[!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span></span>  
  
 <span data-ttu-id="0b336-112">Un mot de prudence est due ici.</span><span class="sxs-lookup"><span data-stu-id="0b336-112">A word of caution is due here.</span></span> <span data-ttu-id="0b336-113">Le `TypeOf...Is` opérateur retourne `True` si un objet est d’un type spécifique, ou est dérivé d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="0b336-113">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="0b336-114">Presque tout ce que vous effectuez avec [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] implique des objets, qui incluent des éléments pas forcément perçues comme des objets, tels que les chaînes et les entiers.</span><span class="sxs-lookup"><span data-stu-id="0b336-114">Almost everything you do with [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="0b336-115">Ces objets sont dérivés et héritent des méthodes de <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0b336-115">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="0b336-116">Lorsqu’il est passé un `Integer` et évaluée avec `Object`, le `TypeOf...Is` opérateur retourne `True`.</span><span class="sxs-lookup"><span data-stu-id="0b336-116">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="0b336-117">L’exemple suivant indique que le paramètre `InParam` est à la fois un `Object` et une `Integer`:</span><span class="sxs-lookup"><span data-stu-id="0b336-117">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 <span data-ttu-id="0b336-118">[!code-vb[VbVbalrOOP&#94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b336-118">[!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span></span>  
  
 <span data-ttu-id="0b336-119">L’exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type d’objet passé dans le `Ctrl` argument.</span><span class="sxs-lookup"><span data-stu-id="0b336-119">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="0b336-120">Le `TestObject` les appels de procédure `ShowType` avec trois différents types de contrôles.</span><span class="sxs-lookup"><span data-stu-id="0b336-120">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="0b336-121">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="0b336-121">To run the example</span></span>  
  
1.  <span data-ttu-id="0b336-122">Créez un nouveau projet d’Application Windows et ajoutez un <xref:System.Windows.Forms.Button>contrôle, un <xref:System.Windows.Forms.CheckBox>contrôle et un <xref:System.Windows.Forms.RadioButton>contrôle au formulaire.</xref:System.Windows.Forms.RadioButton> </xref:System.Windows.Forms.CheckBox> </xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="0b336-122">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="0b336-123">À partir du bouton sur votre formulaire, appelez le `TestObject` procédure.</span><span class="sxs-lookup"><span data-stu-id="0b336-123">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="0b336-124">Ajoutez le code suivant à votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="0b336-124">Add the following code to your form:</span></span>  
  
     <span data-ttu-id="0b336-125">[!code-vb[VbVbalrOOP&#95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b336-125">[!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b336-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b336-126">See Also</span></span>  
 <span data-ttu-id="0b336-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A></span><span class="sxs-lookup"><span data-stu-id="0b336-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></span></span>   
<span data-ttu-id="0b336-128"> [Appel d’une propriété ou méthode à l’aide d’un nom de chaîne](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span><span class="sxs-lookup"><span data-stu-id="0b336-128"> [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span></span>  
<span data-ttu-id="0b336-129"> [Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0b336-129"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="0b336-130"> [If... Puis... Else, instruction](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0b336-130"> [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="0b336-131"> [Type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0b336-131"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="0b336-132"> [Integer (type de données)](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="0b336-132"> [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span></span>
