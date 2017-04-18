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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ff219571de9c76802d3f8d3046cf6b6f9d5be9d5
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-values-visual-basic"></a>Valeurs des variables objets (Visual Basic)
Une variable de la [Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) peuvent faire référence à des données de n’importe quel type. La valeur que vous stockez dans un `Object` variable est conservée quelque part en mémoire, alors que la variable contient un pointeur vers les données.  
  
## <a name="object-classifier-functions"></a>Fonctions classifieur d’objets  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fournit des fonctions qui retournent des informations sur ce qu’un `Object` variable fait référence, comme indiqué dans le tableau suivant.  
  
|Fonction|Retourne la valeur True si la variable objet fait référence à|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A>|Un tableau de valeurs, plutôt qu’une seule valeur|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Type de données Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) valeur ou une chaîne qui peut être interprétée comme une valeur de date et d’heure|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Un objet de type <xref:System.DBNull>qui représente des données manquantes ou inexistantes</xref:System.DBNull>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A>|Un objet d’exception qui dérive de<xref:System.Exception></xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Rien ne](../../../../visual-basic/language-reference/nothing.md), autrement dit, aucun objet n’est assignée à la variable|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Un nombre ou une chaîne pouvant être interprétée comme un nombre|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A>|Un type référence (par exemple, une chaîne, tableau, délégué ou type de classe)|  
  
 Vous pouvez utiliser ces fonctions pour éviter de soumettre une valeur non valide à une opération ou une procédure.  
  
## <a name="typeof-operator"></a>TypeOf, opérateur  
 Vous pouvez également utiliser le [TypeOf, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si une variable objet fait actuellement référence à un type de données spécifique. The `TypeOf`... `Is` l’expression `True` si le type au moment de l’exécution de l’opérande est dérivé ou implémente le type spécifié.  
  
 L’exemple suivant utilise `TypeOf` sur les variables objets faisant référence aux types valeur et référence.  
  
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
  
 L’exemple précédent écrit les lignes suivantes à la **Debug** fenêtre :  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 La variable objet `num` fait référence aux données de type `Integer`, et `frm` fait référence à un objet de classe <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form>  
  
## <a name="object-arrays"></a>Tableaux d’objets  
 Vous pouvez déclarer et utiliser un tableau de `Object` variables. Cela est utile lorsque vous avez besoin gérer une variété de types de données et des classes d’objet. Tous les éléments dans le tableau doivent avoir les mêmes données déclarées de type. Déclaration de type de données `Object` vous permet de stocker des objets et instances de classes parmi d’autres types de données dans le tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Comment : faire référence à l’Instance actuelle d’un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Comment : déterminer le Type désigné par une Variable objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [Comment : déterminer si deux objets sont liés.](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Comment : déterminer si deux objets sont identiques](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
