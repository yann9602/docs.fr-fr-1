---
title: "Variable objet ou variable bloc With non définie | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 820ef0115a6a27d77f10f4e41d95576bbd79bfa3
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a>Variable objet ou variable bloc With non définie
Une variable d’objet non valide est référencée.   Cette erreur peut se produire pour plusieurs raisons :  
  
-   Une variable a été déclarée sans spécification d’un type. Si une variable est déclarée sans spécification d’un type, les valeurs par défaut pour le type `Object`.  
  
     Par exemple, une variable déclarée avec `Dim x` sont de type `Object;` une variable déclarée avec `Dim x As String` sont de type `String`.  
  
    > [!TIP]
    >  Le `Option Strict` instruction n’autorise pas la saisie implicite qui résulte dans une `Object` type. Si vous omettez le type, une erreur de compilation se produit. Consultez la page [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Vous tentez de référencer un objet qui a été défini sur`Nothing`  
  
     .  
  
-   Vous tentez d’accéder à un élément d’une variable tableau qui n’a pas été déclaré correctement.  
  
     Par exemple, un tableau déclaré en tant que `products() As String` déclenche l’erreur si vous essayez de référencer un élément du tableau `products(3) = "Widget"`. Le tableau ne comporte aucun élément et est traité comme un objet.  
  
-   Vous tentez d’accéder au code dans un `With...End With` bloquer avant le bloc a été initialisé.   A `With...End With` doit être initialisé en exécutant le `With` point d’entrée l’instruction.  
  
> [!NOTE]
>  Dans les versions antérieures de Visual Basic ou VBA cette erreur a été également déclenchée en affectant une valeur à une variable sans utiliser le `Set` (mot clé) (`x = "name"` au lieu de `Set x = "name"`). Le `Set` mot clé n’est plus valide dans Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Définissez `Option Strict` à `On` en ajoutant le code suivant au début du fichier :  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  Si vous ne souhaitez pas activer `Option Strict`, recherchez le code de toutes les variables qui ont été spécifiées sans type (`Dim x` au lieu de `Dim x As String`) et ajoutez le type de destination à la déclaration.  
  
3.  Assurez-vous que vous n’êtes pas référence à une variable objet qui a été définie sur `Nothing`.  Recherchez le code pour le mot clé `Nothing`et modifier votre code pour que l’objet n’est pas défini sur `Nothing` jusqu'à ce qu’une fois que vous avez référencé il.  
  
4.  Assurez-vous que toutes les variables tableau sont dimensionnés avant d’y accéder. Vous pouvez attribuer une dimension lorsque vous créez le tableau (`Dim x(5) As String` au lieu de `Dim x() As String`), ou utiliser le `ReDim` (mot clé) pour définir les dimensions du tableau avant tout d’abord accéder.  
  
5.  Assurez-vous que votre `With` est initialisé en exécutant le `With` point d’entrée l’instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration des variables objets](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [With...End With (instruction)](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
