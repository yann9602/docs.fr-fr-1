---
title: "Détermination du type Object (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a63b5cf5941deb4dcc7518880b4dc7d0545803c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="5dee3-102">Détermination du type Object (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5dee3-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="5dee3-103">Les variables objets génériques (autrement dit, les variables que vous déclarez comme `Object`) peuvent contenir les objets à partir de n’importe quelle classe.</span><span class="sxs-lookup"><span data-stu-id="5dee3-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="5dee3-104">Lors de l’utilisation de variables de type `Object`, vous devrez peut-être prendre des mesures différentes selon la classe de l’objet ; par exemple, certains objets ne peuvent pas en charge une propriété ou méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="5dee3-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="5dee3-105">offre deux moyens de déterminer quel type d’objet est stocké dans une variable objet : le `TypeName` (fonction) et le `TypeOf...Is` opérateur.</span><span class="sxs-lookup"><span data-stu-id="5dee3-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="5dee3-106">TypeName et TypeOf... Est</span><span class="sxs-lookup"><span data-stu-id="5dee3-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="5dee3-107">Le `TypeName` fonction retourne une chaîne et est le meilleur choix lorsque vous devez stocker ou afficher le nom de classe d’un objet, comme indiqué dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="5dee3-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="5dee3-108">Le `TypeOf...Is` opérateur est le meilleur choix pour le test d’un type d’objet, car il est beaucoup plus rapide qu’une comparaison de chaîne équivalente à l’aide de `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="5dee3-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="5dee3-109">Le fragment de code suivant utilise `TypeOf...Is` dans un `If...Then...Else` instruction :</span><span class="sxs-lookup"><span data-stu-id="5dee3-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="5dee3-110">Un mot de prudence est due ici.</span><span class="sxs-lookup"><span data-stu-id="5dee3-110">A word of caution is due here.</span></span> <span data-ttu-id="5dee3-111">Le `TypeOf...Is` opérateur retourne `True` si un objet est d’un type spécifique, ou est dérivé d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="5dee3-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="5dee3-112">Presque tout ce que vous effectuez avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] implique des objets, qui incluent des éléments normalement pas considérés comme des objets, tels que les chaînes et les entiers.</span><span class="sxs-lookup"><span data-stu-id="5dee3-112">Almost everything you do with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="5dee3-113">Ces objets sont dérivés et héritent des méthodes de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5dee3-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="5dee3-114">Lorsqu’il est passé un `Integer` et évaluée avec `Object`, le `TypeOf...Is` opérateur retourne `True`.</span><span class="sxs-lookup"><span data-stu-id="5dee3-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="5dee3-115">L’exemple suivant indique que le paramètre `InParam` est à la fois un `Object` et une `Integer`:</span><span class="sxs-lookup"><span data-stu-id="5dee3-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="5dee3-116">L’exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type d’objet passé dans le `Ctrl` argument.</span><span class="sxs-lookup"><span data-stu-id="5dee3-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="5dee3-117">Le `TestObject` les appels de procédure `ShowType` avec trois types différents de contrôles.</span><span class="sxs-lookup"><span data-stu-id="5dee3-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="5dee3-118">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5dee3-118">To run the example</span></span>  
  
1.  <span data-ttu-id="5dee3-119">Créez un nouveau projet d’Application Windows et ajoutez un <xref:System.Windows.Forms.Button> (contrôle), un <xref:System.Windows.Forms.CheckBox> (contrôle) et un <xref:System.Windows.Forms.RadioButton> contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="5dee3-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="5dee3-120">À partir du bouton sur votre formulaire, appelez le `TestObject` procédure.</span><span class="sxs-lookup"><span data-stu-id="5dee3-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="5dee3-121">Ajoutez le code suivant à votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="5dee3-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5dee3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dee3-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [<span data-ttu-id="5dee3-123">Appel d’une propriété ou méthode à l’aide d’un nom de chaîne</span><span class="sxs-lookup"><span data-stu-id="5dee3-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [<span data-ttu-id="5dee3-124">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="5dee3-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="5dee3-125">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="5dee3-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="5dee3-126">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="5dee3-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="5dee3-127">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="5dee3-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
