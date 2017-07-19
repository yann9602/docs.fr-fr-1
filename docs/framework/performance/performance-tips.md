---
title: "Conseils relatifs aux performances .NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage C#, performances"
  - "performance (C#)"
  - "performance (Visual Basic)"
  - "Visual Basic, performances"
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
caps.handback.revision: 36
---
# Conseils relatifs aux performances .NET
Le terme *performance* désigne généralement la vitesse d'exécution d'un programme.  Vous pouvez parfois accroître cette vitesse d'exécution en suivant certaines règles élémentaires dans votre code source.  Dans certains programmes, il est primordial d'examiner avec soin le code et d'utiliser des profileurs pour s'assurer que l'exécution de ce code est aussi rapide que possible.  Dans d'autres programmes, cette optimisation n'est pas nécessaire puisque l'exécution du code est tout aussi acceptable que la qualité de son écriture.  Cet article répertorie quelques zones courantes où les performances peuvent souffrir et des conseils pour les améliorer, ainsi que des liens vers des rubriques de performances supplémentaires.  Pour plus d'informations sur la planification et l'évaluation des performances, consultez [Performance](../../../docs/framework/performance/index.md)  
  
## Conversion boxing et unboxing  
 Il vaut mieux éviter d'utiliser des types valeur dans les cas où ils doivent faire l'objet de nombreuses opérations de boxing, par exemple dans les classes de collections non génériques comme <xref:System.Collections.ArrayList?displayProperty=fullName>.  Vous pouvez éviter le boxing des types valeur en utilisant des collections génériques comme <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  Le boxing et l'unboxing sont des processus très onéreux en calcul.  Lorsqu'un type valeur est converti \(boxed\), un objet entièrement nouveau doit être créé.  Cette opération peut être 20 fois plus longue qu'une simple assignation de référence.  Lors de l'unboxing, le processus de casting peut prendre jusqu'à quatre fois le temps d'une assignation.  Pour plus d'informations, consultez [Conversion boxing et unboxing](../Topic/Boxing%20and%20Unboxing%20\(C%23%20Programming%20Guide\).md).  
  
## Chaînes  
 Lorsque vous concaténez un grand nombre de variables chaîne, par exemple dans une boucle serrée, utilisez <xref:System.Text.StringBuilder?displayProperty=fullName> au lieu de l'[opérateur \+](../Topic/+%20Operator%20\(C%23%20Reference\).md) C\# ou des [opérateurs de concaténation](../Topic/Concatenation%20Operators%20\(Visual%20Basic\).md) Visual Basic.  Pour plus d’informations, consultez [Comment : concaténer plusieurs chaînes](../Topic/How%20to:%20Concatenate%20Multiple%20Strings%20\(C%23%20Programming%20Guide\).md) et [Concatenation Operators in Visual Basic](../Topic/Concatenation%20Operators%20in%20Visual%20Basic.md).  
  
## Destructeurs  
 Les destructeurs vides ne doivent pas être utilisés.  Lorsqu'une classe contient un destructeur, une entrée est créée dans la file d'attente Finalize.  Lorsque le destructeur est appelé, le garbage collector est appelé pour traiter la file d'attente.  Si le destructeur est vide, cela se solde simplement par une perte de performance.  Pour plus d’informations, consultez [Destructeurs](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md) et [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md).  
  
## Autres ressources  
  
-   [Écrire le code managé plus rapidement : connaître le coût des choses \(en anglais\)](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Écrire des applications managées haute performance : initiation \(en anglais\)](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Notions de base et conseils de performance relatifs au Garbage Collector](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [Conseils et astuces relatifs aux performances dans les applications .NET \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=99297)  
  
-   [Outils de diagnostic pour .NET](http://go.microsoft.com/fwlink/?LinkId=112407)  
  
-   [Conseils de performance de Rico Mariani \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=115679)  
  
## Voir aussi  
 [Performance](../../../docs/framework/performance/index.md)   
 [Concepts de programmation](../Topic/Programming%20Concepts.md)   
 [Visual Basic Programming Guide](../Topic/Visual%20Basic%20Programming%20Guide.md)   
 [Guide de programmation C\#](../Topic/C%23%20Programming%20Guide.md)