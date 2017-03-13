---
title: "G&#233;n&#233;riques et attributs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "attributs (C#), avec des génériques"
  - "génériques (C#), attributs"
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# G&#233;n&#233;riques et attributs (Guide de programmation C#)
Les attributs peuvent être appliqués aux types génériques de la même manière qu'aux types non génériques.  Pour plus d'informations sur l'application des attributs, consultez [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Les attributs personnalisés sont uniquement autorisés à référencer des types génériques ouverts, qui sont des types génériques pour lesquels aucun argument de type n'est fourni, et des types génériques construits fermés, qui fournissent des arguments pour tous les paramètres de type.  
  
 Les exemples suivants utilisent cet attribut personnalisé :  
  
 [!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Un attribut peut référencer un type générique ouvert :  
  
 [!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Spécifiez plusieurs paramètres de type à l'aide du nombre approprié de virgules.  Dans cet exemple, `GenericClass2` a deux paramètres de type :  
  
 [!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Un attribut peut référencer un type générique construit fermé :  
  
 [!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Un attribut qui référence un paramètre de type générique entraînera une erreur de compilation :  
  
 [!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Un type générique ne peut pas hériter de <xref:System.Attribute> :  
  
 [!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Pour obtenir des informations à propos d'un type générique ou d'un paramètre de type au moment de l'exécution, vous pouvez utiliser les méthodes de <xref:System.Reflection>.  Pour plus d'informations, consultez [Génériques et réflexion](../../../csharp/programming-guide/generics/generics-and-reflection.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Attributs](../Topic/Extending%20Metadata%20Using%20Attributes.md)