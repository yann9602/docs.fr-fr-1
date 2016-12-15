---
title: "How to: Declare a Structure (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "declarations, structures"
  - "structure statements"
  - "statements [Visual Basic], structure"
  - "structures, declaring"
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare a Structure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Commencez une déclaration de structure par l'instruction Structure \([Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)\) et terminez\-la par `End` `Structure`.  Entre ces deux instructions, vous devez déclarer au moins un *élément*.  Les éléments peuvent être de tout type de données, mais au moins un d'entre eux doit être une variable non partagée ou un événement non partagé et non personnalisé.  
  
 Vous ne pouvez initialiser aucun des éléments de structure dans la déclaration de structure.  Lorsque vous déclarez une variable comme étant d'un type structure, vous assignez des valeurs aux éléments en y accédant par l'intermédiaire de la variable.  
  
 Pour une discussion des différences entre les structures et les classes, consultez [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 À des fins de démonstration, considérez une situation dans laquelle vous souhaitez assurer le suivi du nom, du poste téléphonique et du salaire d'un employé.  Une structure vous permet d'effectuer cette opération dans une seule variable.  
  
### Pour déclarer une structure  
  
1.  Créez les instructions de début et de fin de la structure.  
  
     Vous pouvez spécifier le niveau d'accès d'une structure à l'aide du mot clé [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Private](../../../../visual-basic/language-reference/modifiers/private.md), ou vous pouvez accepter le paramètre par défaut, `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Ajoutez des éléments au corps de la structure.  
  
     Une structure doit avoir au moins un élément.  Vous devez déclarer chaque élément et spécifier pour lui un niveau d'accès.  Si vous utilisez l'instruction Dim \([Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)\) sans mot clé, l'accessibilité prend la valeur par défaut, `Public`.  
  
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
  
     Le champ `salary` dans l'exemple précédent est `Private`, ce qui signifie qu'il est inaccessible à l'extérieur de la structure, même à partir de la classe conteneur.  Toutefois, la procédure `giveRaise` étant de type `Public`, elle peut être appelée de l'extérieur de la structure.  De même, vous pouvez déclencher l'événement `salaryReviewTime` depuis l'extérieur de la structure.  
  
     En plus des variables, des procédures `Sub` et des événements, vous pouvez également définir des constantes, des procédures `Function` et des propriétés dans une structure.  Vous pouvez désigner au plus une propriété comme *propriété par défaut*, à condition qu'elle accepte au moins un argument.  Vous pouvez gérer un événement avec une procédure `Sub` [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).  Pour plus d'informations, consultez [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [User\-Defined Data Type](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)