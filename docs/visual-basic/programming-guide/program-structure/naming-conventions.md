---
title: "Visual Basic Naming Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "names, Visual Basic rules"
  - "naming conventions"
  - "naming conventions, Visual Basic"
  - "Visual Basic code, naming conventions"
  - "conventions, Visual Basic coding"
  - "names, naming conventions"
  - "naming conventions, classes"
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic Naming Conventions
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsque vous nommez un élément de votre application Visual Basic, le premier caractère de ce nom doit être un caractère alphanumérique ou un trait de soulignement.  Toutefois, notez que les noms commençant par un trait de soulignement ne sont pas conformes avec la [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\).  
  
 Les suggestions suivantes s'appliquent à l'affectation de noms :  
  
-   Faites commencer chaque mot distinct d'un nom par une majuscule, par exemple `FindLastRecord` et `RedrawMyForm`.  
  
-   Faites commencer les noms de fonctions et de méthodes par un verbe, comme dans `InitNameArray` ou `CloseDialog`.  
  
-   Faites commencer les noms de classes, de structures, de modules et de propriétés par un nom, comme dans `EmployeeName` ou `CarAccessory`.  
  
-   Faites commencer les noms de l'interface par le préfixe « I », suivi d'un nom ou d'une expression nominale \(par exemple, `IComponent`\) ou d'un adjectif décrivant le comportement de l'interface \(par exemple, `IPersistable`\).  N'utilisez pas le trait de soulignement et évitez autant que possible les abréviations, qui sont source de confusion.  
  
-   Faites commencer les noms de gestionnaires d'événements par un nom décrivant le type d'événements, suivi du suffixe « `EventHandler` », par exemple « `MouseEventHandler` ».  
  
-   Dans les noms de classes d'arguments d'événements, ajoutez le suffixe « `EventArgs` ».  
  
-   Si un événement contient une notion d'antériorité ou de postériorité, utilisez un suffixe décliné au présent ou au passé, par exemple « `ControlAdd` » ou « `ControlAdded` ».  
  
-   Pour les termes longs ou fréquemment utilisés, utilisez des abréviations afin d'en limiter la longueur, par exemple « HTML » au lieu de « Hypertext Markup Language ».  D'une manière générale, les noms de variables d'une longueur supérieure à 32 caractères sont difficiles à lire sur un écran avec une résolution basse.  Assurez\-vous également que vos abréviations sont cohérentes dans toute l'application.  En effet, le fait d'utiliser indifféremment « HTML » et « Hypertext Markup Language » ne peut être que source de confusion.  
  
-   Évitez d'utiliser dans une portée interne les mêmes noms que dans une portée externe.  Des erreurs peuvent être générées en cas d'accès à la mauvaise variable.  En cas de conflit entre une variable et le mot clé du même nom, vous devez identifier le mot clé en le faisant précéder de la bibliothèque de types appropriée.  Par exemple, si l'une de vos variables porte le nom `Date`, vous ne pouvez utiliser la fonction `Date` intrinsèque qu'en appelant <xref:System.DateTime.Date%2A?displayProperty=fullName>.  
  
## Voir aussi  
 [Keywords as Element Names in Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)