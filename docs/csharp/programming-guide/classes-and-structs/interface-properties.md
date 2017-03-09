---
title: "Propri&#233;t&#233;s d&#39;interface (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "interfaces (C#), propriétés"
  - "propriétés (C#), sur des interfaces"
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# Propri&#233;t&#233;s d&#39;interface (Guide de programmation C#)
Les propriétés peuvent être déclarées sur une [interface](../../../csharp/language-reference/keywords/interface.md).  Exemple d'accesseur d'indexeur d'interface :  
  
 [!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/interface-properties_1.cs)]  
  
 L'accesseur d'une propriété d'interface ne possède pas de corps.  Ainsi, les accesseurs ont pour objet d'indiquer si la propriété est en lecture\-écriture, en écriture seule ou en lecture seule.  
  
## Exemple  
 Dans cet exemple, l'interface `IEmployee` possède une propriété en lecture\-écriture, `Name`, et une propriété en lecture seule, `Counter`.  La classe `Employee` implémente l'interface `IEmployee` et utilise ces deux propriétés.  Le programme lit le nom d'un nouvel employé et le nombre actuel d'employés, puis affiche le nom de l'employé et le nombre d'employés calculé.  
  
 Vous pourriez utiliser le nom complet de la propriété, qui fait référence à l'interface dans laquelle le membre est déclaré.  Par exemple :  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/interface-properties_2.cs)]  
  
 C'est ce qu'on appelle [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  Par exemple, si la classe `Employee` implémente deux interfaces `ICitizen` et `IEmployee`, et que ces deux interfaces possèdent la propriété `Name`, l'implémentation explicite des membres d'interface est nécessaire.  Ainsi, la déclaration de propriété suivante :  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/interface-properties_2.cs)]  
  
 implémente la propriété `Name` sur l'interface `IEmployee`, tandis que la déclaration :  
  
 [!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/interface-properties_3.cs)]  
  
 implémente la propriété `Name` sur l'interface `ICitizen`.  
  
 [!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## Résultat de l'exemple  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Comparaison entre propriétés et indexeurs](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)