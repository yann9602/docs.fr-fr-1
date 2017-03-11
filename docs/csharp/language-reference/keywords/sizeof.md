---
title: "sizeof (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "sizeof_CSharpKeyword"
  - "sizeof"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sizeof (mot clé C#)"
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# sizeof (r&#233;f&#233;rence C#)
Utilisé pour obtenir la taille en octets d'un type non managé.  Les types non managés incluent les types intégrés répertoriés dans le tableau suivant, et également les éléments suivants :  
  
-   Types d'enum  
  
-   Types de pointeur  
  
-   Les structs définis par l'utilisateur qui ne contiennent pas tous les champs ou propriétés qui sont des types référence  
  
 L'exemple suivant indique comment extraire la taille d'un `int` :  
  
```c#  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## Notes  
 Depuis la version 2.0 de C\#, appliquer `sizeof` à des types intégrés n'oblige plus à utiliser le mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 L'opérateur `sizeof` ne peut pas être surchargé.  Les valeurs retournées par l'opérateur `sizeof` sont de type `int`.  Le tableau suivant montre les valeurs de constantes substituées aux expressions `sizeof` qui ont certains types intégrés en tant qu'opérandes.  
  
|Expression|Valeur de constante|  
|----------------|-------------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 \(Unicode\)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 Pour tous les autres types, y compris les structs, l'opérateur `sizeof` ne peut être utilisé que dans des blocs de code unsafe.  Bien que vous puissiez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName>, la valeur retournée par cette méthode n'est pas toujours la même que celle retournée par `sizeof`.  <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> retourne la taille après avoir marshalé le type, alors que `sizeof` retourne la taille comme elle a été allouée par le common language runtime, y compris tout remplissage.  
  
## Exemple  
 [!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#11)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [enum](../../../csharp/language-reference/keywords/enum.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Structures](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)