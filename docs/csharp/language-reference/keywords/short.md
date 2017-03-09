---
title: "short (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "short"
  - "short_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "short (mot clé C#)"
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# short (r&#233;f&#233;rence C#)
Le mot clé `short` désigne un type intégral ; il est utilisé pour stocker des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`short`|\-32 768 à 32 767|Entier 16 bits signé|<xref:System.Int16?displayProperty=fullName>|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `short` en suivant l'exemple ci\-après :  
  
```  
  
short x = 32767;  
```  
  
 Dans la déclaration précédente, le littéral entier `32767` est implicitement converti de type [int](../../../csharp/language-reference/keywords/int.md) en type `short`.  Si le littéral entier a une taille de stockage supérieure à la taille maximale définie par `short`, une erreur de compilation se produit.  
  
 Une conversion doit être utilisée lors de l'appel de méthodes surchargées.  Prenez l'exemple suivant de deux méthodes surchargées ayant pour paramètres `short` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 Le recours à un cast `short` permet de garantir que le type correct sera appelé, comme indiqué ci\-après :  
  
```  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## Conversions  
 Il y a une conversion implicite prédéfinie de `short` en [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Il n'est pas possible de convertir implicitement en `short` des types numériques non littéraux d'une taille de stockage supérieure \(consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour plus d'informations sur les tailles de stockage des types intégraux\).  Prenez l'exemple suivant de deux variables `short`, `x` et `y` :  
  
```  
  
short x = 5, y = 12;  
```  
  
 L'instruction d'assignation suivante entraîne une erreur de compilation, car l'expression arithmétique située à droite de l'opérateur d'assignation a pour résultat [int](../../../csharp/language-reference/keywords/int.md)par défaut.  
  
 `short`   `z = x + y;   // Error: no conversion from int to short`  
  
 Pour résoudre ce problème, utilisez une conversion explicite :  
  
 `short`   `z = (`  `short`  `)(x + y);   // OK: explicit conversion`  
  
 Il est cependant possible d'utiliser les instructions suivantes dans lesquelles la variable de destination possède une taille de stockage égale ou supérieure :  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 En outre, il n'y a pas de conversion implicite des types en virgule flottante en type `short`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
  
        short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d'informations sur les règles de conversion numérique implicite, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.Int16>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)