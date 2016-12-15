---
title: "Constructeurs (guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "constructeurs [C#]"
  - "classes [C#], constructeurs"
  - "langage C#, constructeurs"
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Constructeurs (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

À chaque fois qu'une [classe](../../../csharp/language-reference/keywords/class.md) ou qu'un [struct](../../../csharp/language-reference/keywords/struct.md) est créé, son constructeur est appelé.  Une classe ou un struct peut avoir plusieurs constructeurs qui prennent des arguments différents.  Les constructeurs permettent au programmeur de définir des valeurs par défaut, de limiter l'instanciation et d'écrire un code souple d'utilisation et facile à lire.  Pour plus d'informations et d'exemples, consultez [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) et [Constructeurs d'instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Si vous ne fournissez pas de constructeur pour votre objet, C\# en créera un par défaut qui instanciera l'objet et affectera à toutes les variables membres les valeurs par défaut répertoriées dans [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  Pour plus d'informations et d'exemples, consultez [Constructeurs d'instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Les classes et structs statiques peuvent également avoir des constructeurs.  Pour plus d'informations et d'exemples, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## Dans cette section  
 [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Constructeurs d'instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Constructeurs privés](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Comment : écrire un constructeur de copie](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [statiques](../../../csharp/language-reference/keywords/static.md)   
 [Pourquoi les initialiseurs fonctionnent\-ils dans l'ordre opposée comme constructeurs ? Première partie](http://go.microsoft.com/fwlink/?LinkId=112374)