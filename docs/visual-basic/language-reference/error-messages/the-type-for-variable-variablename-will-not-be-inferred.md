---
title: "Le type de variable &quot;&lt;variablename&gt;» ne sera pas déduit, car il est lié à un champ dans une portée englobante | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ab7d69c34a58dc898553868258c4fdf6b81db343
ms.lasthandoff: 03/13/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Le type de variable '&lt;variablename&gt;» ne sera pas déduit, car il est lié à un champ dans une portée englobante
Le type de variable '\<variablename > » ne sera pas déduit, car il est lié à un champ dans une portée englobante. Modifiez le nom de «\<variablename > », ou utilisez le nom qualifié complet (par exemple, 'Me.NomVariable' ou 'MyBase.NomVariable').  
  
 Une variable de contrôle de boucle dans votre code a le même nom qu’un champ de la classe ou une autre portée englobante. Étant donné que la variable de contrôle est utilisée sans un `As` clause, elle est liée au champ dans la portée englobante, et le compilateur ne pas créer une variable pour lui ou déduire son type.  
  
 Dans l’exemple suivant, `Index`, la variable de contrôle dans les `For` instruction, est lié à la `Index` champ la `Customer` classe. Le compilateur ne crée pas de variable pour la variable de contrôle `Index` ou déduire son type.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
  
```  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou de considérer les avertissements comme des erreurs, consultez [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42110  
  
### <a name="to-address-this-warning"></a>Pour traiter cet avertissement  
  
-   Vérifiez la variable de contrôle de boucle local en modifiant son nom à un identificateur qui n’est pas le nom d’un champ de la classe.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Précisez que la variable de contrôle de boucle crée une liaison pour le champ de classe en ajoutant le préfixe `Me.` au nom de variable.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Au lieu de compter sur l’inférence de type local, utilisez un `As` clause pour spécifier un type pour la variable de contrôle de boucle.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Exemple  
 Le code suivant montre l’exemple précédent avec la première correction en place.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [For Each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Pour... Instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Comment : faire référence à l’Instance actuelle d’un objet](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Inférence de Type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me, My, MyBase et MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
