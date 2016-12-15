---
title: "Efficient Use of Data Types (Visual Basic) | Microsoft Docs"
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
  - "performance, data type efficiency"
  - "data types [Visual Basic], weak typing"
  - "AscW function, preferred to Asc"
  - "data types [Visual Basic], using efficiently"
  - "optimization, data types"
  - "data types [Visual Basic], strong typing"
  - "strong typing"
  - "typing, strong"
  - "data types [Visual Basic], optimizing"
  - "ChrW function, preferred to Chr"
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Efficient Use of Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les variables non déclarées et celles qui sont déclarées sans type de données prennent le type de données `Object`.  Vous pouvez ainsi écrire plus facilement et rapidement des programmes, mais leur exécution sera plus lente.  
  
## Typage fort  
 Le processus qui consiste à spécifier des types de données pour toutes les variables est appelé *typage fort*.  Le typage fort présente plusieurs avantages :  
  
-   Il active la prise en charge IntelliSense pour vos variables.  Il vous permet de voir leurs propriétés et leurs autres membres à mesure que vous tapez le code.  
  
-   Tire parti du contrôle de type de compilateur.  Il intercepte les instructions susceptibles de provoquer, au moment de l'exécution, des erreurs telles qu'un dépassement de capacité.  Il intercepte également les appels aux méthodes dans des objets qui ne les prennent pas en charge.  
  
-   Il permet ainsi à votre code de s'exécuter plus rapidement.  
  
## Types de données les plus efficaces  
 Pour les variables qui ne contiennent jamais de fractions, les types de données intégraux sont plus efficaces que les types non intégraux.  En [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` et `UInteger` sont les types numériques les plus efficaces.  
  
 Pour les nombres fractionnaires, `Double` est le type de données le plus efficace, parce que les processeurs sur les plateformes actuelles exécutent des opérations en virgule flottante double précision.  Toutefois, les opérations avec `Double` ne sont pas aussi rapides qu'avec les types intégraux, tels que `Integer`.  
  
## Spécifier le type de données  
 Faites appel à [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) pour déclarer une variable d'un type spécifique.  Vous pouvez spécifier simultanément son niveau d'accès à l'aide du mot clé [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Private](../../../../visual-basic/language-reference/modifiers/private.md), comme dans l'exemple suivant.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## Conversion des caractères  
 Les fonctions `AscW` et `ChrW` opèrent en Unicode.  Utilisez\-les de préférence à `Asc` et `Chr` qui doivent traduire en Unicode ou à partir de ce format.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Utilisation de la fonctionnalité IntelliSense](/visual-studio/ide/using-intellisense)