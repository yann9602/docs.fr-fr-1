---
title: "How to: Declare Enumerations (Visual Basic) | Microsoft Docs"
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
  - "declarations, enumerations"
  - "enumerations [Visual Basic], declaring"
  - "declaring enumerations"
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# How to: Declare Enumerations (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'ajout d'une instruction `Enum` dans la section des déclarations d'une classe ou d'un module permet de créer une énumération.  Vous ne pouvez pas déclarer d'énumération dans une méthode.  Pour spécifier le niveau d'accès approprié, utilisez `Private`, `Protected`, `Friend` ou `Public`.  
  
 Un type `Enum` possède un nom, un type sous\-jacent et un ensemble de champs, dont chacun représente une constante.  Le nom doit être un qualificateur [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] valide.  Le type sous\-jacent doit correspondre à l'un des types d'entiers : `Byte`, `Short`, `Long` ou `Integer`.  `Integer` est la valeur par défaut.  Les énumérations sont toujours fortement typées et ne sont pas interchangeables avec les types de nombre entier.  
  
 Les énumérations ne peuvent pas comporter de valeurs à virgule flottante.  Si une valeur à virgule flottante avec `Option Strict On` est assignée à une énumération, une erreur de compilation se produit.  Si `Option Strict` est `Off`, la valeur est convertie automatiquement en type `Enum`.  
  
 Pour plus d'informations sur les noms et sur l'utilisation de l'instruction `Imports` pour rendre inutile la qualification de noms, consultez [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### Pour déclarer une énumération  
  
1.  Écrivez une déclaration qui inclut un niveau d'accès de code, le mot clé `Enum` et un nom valide, comme dans les exemples suivants, qui déclarent chacun un `Enum` différent.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#3)]  
  
2.  Définissez les constantes dans l'énumération.  Par défaut, la première constante d'une énumération est initialisée à la valeur `0` et les constantes suivantes sont initialisées à une valeur de plus que la constante précédente.  Par exemple, l'énumération suivante \(`Days`\) contient une constante nommée `Sunday` avec la valeur `0`, une constante nommée `Monday` avec la valeur `1`, une constante nommée `Tuesday` avec la valeur `2`, et ainsi de suite.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#4)]  
  
3.  Vous pouvez assigner explicitement des valeurs à des constantes dans une énumération en utilisant une instruction d'assignation.  Vous pouvez assigner une valeur entière, y compris des nombres négatifs.  Par exemple, vous pouvez définir des constantes avec des valeurs inférieures à zéro pour représenter des conditions d'erreur.  Dans l'énumération suivante, la valeur `–1` est explicitement assignée à la constante `Invalid` et la valeur `0` est assignée à la constante `Sunday`.  Dans la mesure où `Saturday` est la première constante de l'énumération, la valeur `0` lui est également assignée.  La valeur de `Monday` est `1` \(un de plus que la valeur de `Sunday`\), la valeur de `Tuesday` est `2`, et ainsi de suite.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#5)]  
  
### Pour déclarer une énumération en tant que type explicite  
  
-   Spécifiez le type de l'énumération à l'aide de la clause `As`, comme indiqué dans l'exemple suivant.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#6)]  
  
## Voir aussi  
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)