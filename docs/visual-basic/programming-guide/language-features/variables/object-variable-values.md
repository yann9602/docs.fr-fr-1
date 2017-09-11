---
title: "Valeurs des variables (Visual Basic) de l’objet | Documents Microsoft"
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
- object variables, values
- values, of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
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
ms.openlocfilehash: 5f42706a79212ae523b08ee336fdcacb3f761af6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="4a15b-102">Valeurs des variables objets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a15b-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="4a15b-103">Une variable de la [Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) peuvent faire référence à des données de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="4a15b-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="4a15b-104">La valeur que vous stockez dans un `Object` variable est conservée quelque part en mémoire, alors que la variable contient un pointeur vers les données.</span><span class="sxs-lookup"><span data-stu-id="4a15b-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="4a15b-105">Fonctions classifieur d’objets</span><span class="sxs-lookup"><span data-stu-id="4a15b-105">Object Classifier Functions</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4a15b-106">Fournit des fonctions qui retournent des informations sur ce qu’un `Object` variable fait référence, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="4a15b-106"> supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="4a15b-107">Fonction</span><span class="sxs-lookup"><span data-stu-id="4a15b-107">Function</span></span>|<span data-ttu-id="4a15b-108">Retourne la valeur True si la variable objet fait référence à</span><span class="sxs-lookup"><span data-stu-id="4a15b-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<span data-ttu-id="4a15b-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></span></span>|<span data-ttu-id="4a15b-110">Un tableau de valeurs, plutôt qu’une seule valeur</span><span class="sxs-lookup"><span data-stu-id="4a15b-110">An array of values, rather than a single value</span></span>|  
|<span data-ttu-id="4a15b-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></span></span>|<span data-ttu-id="4a15b-112">A [Type de données Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) valeur ou une chaîne qui peut être interprétée comme une valeur de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="4a15b-112">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<span data-ttu-id="4a15b-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span></span>|<span data-ttu-id="4a15b-114">Un objet de type <xref:System.DBNull>qui représente des données manquantes ou inexistantes</xref:System.DBNull></span><span class="sxs-lookup"><span data-stu-id="4a15b-114">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<span data-ttu-id="4a15b-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></span></span>|<span data-ttu-id="4a15b-116">Un objet d’exception qui dérive de<xref:System.Exception></xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="4a15b-116">An exception object, which derives from <xref:System.Exception></span></span>|  
|<span data-ttu-id="4a15b-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></span></span>|<span data-ttu-id="4a15b-118">[Rien ne](../../../../visual-basic/language-reference/nothing.md), autrement dit, aucun objet n’est assignée à la variable</span><span class="sxs-lookup"><span data-stu-id="4a15b-118">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<span data-ttu-id="4a15b-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span></span>|<span data-ttu-id="4a15b-120">Un nombre ou une chaîne pouvant être interprétée comme un nombre</span><span class="sxs-lookup"><span data-stu-id="4a15b-120">A number, or a string that can be interpreted as a number</span></span>|  
|<span data-ttu-id="4a15b-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A></span><span class="sxs-lookup"><span data-stu-id="4a15b-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></span></span>|<span data-ttu-id="4a15b-122">Un type référence (par exemple, une chaîne, tableau, délégué ou type de classe)</span><span class="sxs-lookup"><span data-stu-id="4a15b-122">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="4a15b-123">Vous pouvez utiliser ces fonctions pour éviter de soumettre une valeur non valide à une opération ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="4a15b-123">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="4a15b-124">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="4a15b-124">TypeOf Operator</span></span>  
 <span data-ttu-id="4a15b-125">Vous pouvez également utiliser le [TypeOf, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si une variable objet fait actuellement référence à un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="4a15b-125">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="4a15b-126">The `TypeOf`... `Is` l’expression `True` si le type au moment de l’exécution de l’opérande est dérivé ou implémente le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a15b-126">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="4a15b-127">L’exemple suivant utilise `TypeOf` sur les variables objets faisant référence aux types valeur et référence.</span><span class="sxs-lookup"><span data-stu-id="4a15b-127">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="4a15b-128">L’exemple précédent écrit les lignes suivantes à la **Debug** fenêtre :</span><span class="sxs-lookup"><span data-stu-id="4a15b-128">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="4a15b-129">La variable objet `num` fait référence aux données de type `Integer`, et `frm` fait référence à un objet de classe <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="4a15b-129">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="4a15b-130">Tableaux d’objets</span><span class="sxs-lookup"><span data-stu-id="4a15b-130">Object Arrays</span></span>  
 <span data-ttu-id="4a15b-131">Vous pouvez déclarer et utiliser un tableau de `Object` variables.</span><span class="sxs-lookup"><span data-stu-id="4a15b-131">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="4a15b-132">Cela est utile lorsque vous avez besoin gérer une variété de types de données et des classes d’objet.</span><span class="sxs-lookup"><span data-stu-id="4a15b-132">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="4a15b-133">Tous les éléments dans le tableau doivent avoir les mêmes données déclarées de type.</span><span class="sxs-lookup"><span data-stu-id="4a15b-133">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="4a15b-134">Déclaration de type de données `Object` vous permet de stocker des objets et instances de classes parmi d’autres types de données dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="4a15b-134">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a15b-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a15b-135">See Also</span></span>  
 <span data-ttu-id="4a15b-136">[Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-136">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="4a15b-137"> [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-137"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="4a15b-138"> [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-138"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="4a15b-139"> [Comment : faire référence à l’Instance actuelle d’un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-139"> [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="4a15b-140"> [Comment : déterminer le Type désigné par une Variable objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-140"> [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span></span>  
<span data-ttu-id="4a15b-141"> [Comment : déterminer si deux objets sont liés.](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-141"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="4a15b-142"> [Comment : déterminer si deux objets sont identiques](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span><span class="sxs-lookup"><span data-stu-id="4a15b-142"> [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span></span>  
<span data-ttu-id="4a15b-143"> [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="4a15b-143"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
