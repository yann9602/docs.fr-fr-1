---
title: "When to Use an Enumeration (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "enumerations [Visual Basic]"
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# When to Use an Enumeration (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les énumérations facilitent l'utilisation des ensembles de constantes connexes.  Une énumération, ou `Enum`, est un nom symbolique pour un ensemble de valeurs.  Les énumérations sont traitées comme des types de données et vous pouvez les utiliser pour créer des jeux de constantes utilisables avec des variables et des propriétés.  
  
## Quand utiliser une énumération  
 À chaque fois qu'une procédure accepte un jeu limité de variables, envisagez d'utiliser une énumération.  Les énumérations rendent le code plus propre et plus lisible, en particulier lorsque des noms explicites sont utilisés.  
  
 Les avantages liés à l'utilisation d'énumérations sont les suivants :  
  
-   elle permet de réduire les erreurs dues à la transposition ou à l'entrée incorrecte de nombres ;  
  
-   elle facilite la modification ultérieure des valeurs ;  
  
-   elle augmente la lisibilité du code, ce qui réduit le risque d'erreurs ;  
  
-   elle garantit la compatibilité ascendante.  Avec les énumérations, votre code est moins susceptible d'échouer si dans l'avenir quelqu'un modifie les valeurs correspondent aux noms de membres.  
  
## Affectation de noms aux énumérations  
 Utilisez une convention d'affectation de noms pour les membres d'énumération.  Lorsque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] rencontre un nom de membre d'énumération, une exception peut être levée si d'autres bibliothèques de types référencées contiennent le même nom.  Utilisez un préfixe unique qui identifie les valeurs de votre application ou composant.  
  
 Lorsque vous faites référence à un membre d'une énumération, vous devez qualifier le nom du membre avec le nom d'énumération ou utiliser l'instruction `Imports`.  Pour plus d'informations, consultez [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## Énumérations prédéfinies  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit plusieurs énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResult`, pour faciliter l'écriture de code.  Pour obtenir une liste de ces énumérations, consultez [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## Voir aussi  
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)