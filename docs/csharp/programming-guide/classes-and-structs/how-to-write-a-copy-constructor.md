---
title: "Comment&#160;: &#233;crire un constructeur de copie (Guide de programmation C#) | Microsoft Docs"
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
  - "Langage C#, constructeur de copie"
  - "constructeur de copie (C#)"
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: &#233;crire un constructeur de copie (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous\-même.  
  
## Exemple  
 Dans l'exemple suivant, la classe `Person` [](../../../csharp/language-reference/keywords/class.md "class (C# Reference)") définit un constructeur de copie qui accepte comme argument une instance de `Person`.  Les valeurs des propriétés de l'argument sont assignées aux propriétés de la nouvelle instance `Person`.  Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l'instance que vous voulez copier au constructeur d'instance de la classe.  
  
 [!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## Voir aussi  
 <xref:System.ICloneable>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)