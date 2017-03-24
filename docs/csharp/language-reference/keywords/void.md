---
title: "void (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "void_CSharpKeyword"
  - "void"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "void (mot clé C#)"
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# void (R&#233;f&#233;rence C#)
Si utilisé comme type de retour d'une méthode, `void` spécifie que la méthode ne retourne pas de valeur.  
  
 n'est pas autorisée`void` dans la liste de paramètres d'une méthode.  Une méthode sans paramètres qui ne retourne aucune valeur se déclare comme suit :  
  
```  
public void SampleMethod()  
{  
    // Body of the method.  
}  
  
```  
  
 `void` est également utilisé dans un contexte non sécurisé pour déclarer un pointeur vers un type inconnu.  Pour plus d'informations, consultez [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
 `void` est un alias pour le type <xref:System.Void?displayProperty=fullName> .NET Framework.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)