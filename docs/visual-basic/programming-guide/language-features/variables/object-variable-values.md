---
title: "Object Variable Values (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, values"
  - "values, of object variables"
  - "data types [Visual Basic], object variable"
  - "variables [Visual Basic], object"
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object Variable Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une variable du type de données Object \([Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)\) peut faire référence à des données de n'importe quel type.  La valeur que vous stockez dans une variable `Object` est conservée quelque part en mémoire, alors que la variable contient un pointeur vers les données.  
  
## Fonctions classifieur d'objets  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit des fonctions qui retournent des informations sur les éléments auxquels une variable `Object` fait référence, comme illustré dans le tableau suivant.  
  
|Fonction|Retourne True si la variable objet fait référence à|  
|--------------|---------------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Un tableau de valeurs au lieu d'une valeur unique|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Une valeur [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) ou une chaîne pouvant être interprétée comme une valeur associée à la date et l'heure|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Un objet de type <xref:System.DBNull> qui représente des données manquantes ou inexistantes|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Un objet d'exception qui dérive de <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nothing](../../../../visual-basic/language-reference/nothing.md) signifie qu'il n'y a pas d'objet actuellement assigné à la variable|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Un nombre ou une chaîne pouvant être interprété comme un nombre|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Un type référence \(tel qu'une chaîne, un tableau, un délégué ou un type classe\)|  
  
 Vous pouvez utiliser ces fonctions pour éviter de soumettre une valeur non valide à une opération ou une procédure.  
  
## TypeOf, opérateur  
 Vous pouvez également utiliser [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si une variable objet fait actuellement référence à un type de données spécifique.  L'expression `TypeOf`...`Is` prend la valeur `True` si le type d'exécution de l'opérande est dérivé du type spécifié ou qu'il implémente celui\-ci.  
  
 L'exemple suivant utilise `TypeOf` sur les variables objets qui font référence aux types valeur et référence.  
  
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
  
 L'exemple précédent écrit les lignes suivantes dans la fenêtre de **débogage** :  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 La variable objet `num` fait référence aux données de type `Integer`, et `frm` fait référence à un objet de la classe <xref:System.Windows.Forms.Form>.  
  
## Tableaux d'objets  
 Vous pouvez déclarer et utiliser un tableau de variables `Object`.  Cela peut vous être utile lorsque vous devez gérer plusieurs types de données et classes d'objets.  Tous les éléments d'un tableau doivent posséder le même type de données déclaré.  En déclarant le type de données `Object`, vous pouvez stocker des objets et des instances de classes parmi d'autres types de données dans le tableau.  
  
## Voir aussi  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)