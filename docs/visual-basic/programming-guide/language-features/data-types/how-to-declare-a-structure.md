---
title: "Comment : déclarer une structure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8203327e189d095c9f7ceeb3b68ea24efe9ba882
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Comment : déclarer une structure (Visual Basic)
Vous commencez une déclaration de structure par le [instruction Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), et vous la terminez avec la `End` `Structure` instruction. Entre ces deux instructions, vous devez déclarer au moins un *élément*. Les éléments peuvent être de n’importe quel type de données, mais au moins doit être une variable non partagée ou un événement non partagé.  
  
 Vous ne peut pas initialiser un des éléments de structure dans la déclaration de structure. Lorsque vous déclarez une variable qui doit être d’un type structure, vous affectez des valeurs aux éléments en y accédant via la variable.  
  
 Pour en savoir plus sur les différences entre les classes et structures, consultez [Structures et Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 À des fins de démonstration, considérez une situation dans laquelle vous souhaitez effectuer le suivi de nom d’un employé, numéro de poste et salaire. Une structure vous permet de procéder à une variable.  
  
### <a name="to-declare-a-structure"></a>Pour déclarer une structure  
  
1.  Créer de début et fin des instructions pour la structure.  
  
     Vous pouvez spécifier le niveau d’accès d’une structure à l’aide de la [Public](../../../../visual-basic/language-reference/modifiers/public.md), [protégé](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privé](../../../../visual-basic/language-reference/modifiers/private.md) (mot clé), ou vous pouvez la laisser par défaut `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Ajouter des éléments dans le corps de la structure.  
  
     Une structure doit avoir au moins un élément. Vous devez déclarer chaque élément et lui attribuer un niveau d’accès. Si vous utilisez la [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sans les mots clés, l’accessibilité par défaut est `Public`.  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     Le `salary` champ dans l’exemple précédent est `Private`, ce qui signifie qu’il n’est pas accessible en dehors de la structure, même à partir de la classe conteneur. Toutefois, le `giveRaise` procédure est `Public`, donc il peut être appelée à l’extérieur de la structure. De même, vous pouvez déclencher la `salaryReviewTime` événement à partir de l’extérieur de la structure.  
  
     En plus des variables, `Sub` des procédures et des événements, vous pouvez également définir des constantes, `Function` des procédures et des propriétés dans une structure. Vous pouvez désigner au plus une propriété comme le *propriété par défaut*, à condition qu’elle accepte au moins un argument. Vous pouvez gérer un événement avec un [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procédure. Pour plus d’informations, consultez [Comment : déclarer et appeler une propriété par défaut en Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Variables de structure](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Type de données défini par l’utilisateur](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
