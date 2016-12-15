---
title: "long (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "long_CSharpKeyword"
  - "long"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "long (mot clé C#)"
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# long (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `long` désigne un type intégral ; il est utilisé pour stocker des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`long`|–9,223,372,036,854,775,808 à 9,223,372,036,854,775,807|Entier 64 bits signé|<xref:System.Int64?displayProperty=fullName>|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `long` en suivant l'exemple ci\-après :  
  
```  
  
long long1 = 4294967296;  
```  
  
 Lorsqu'un littéral entier n'a aucun suffixe, son type est le premier des types dans lesquels sa valeur peut être représentée : [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), `long`, [ulong](../../../csharp/language-reference/keywords/ulong.md).  Dans l'exemple précédent, il est de type `long`, car il dépasse la plage de [uint](../../../csharp/language-reference/keywords/uint.md) \(consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour les tailles de stockage de types intégraux\).  
  
 Vous pouvez aussi utiliser le suffixe L avec le type `long`, comme suit :  
  
```  
  
long long2 = 4294967296L;  
```  
  
 Lorsque vous utilisez le suffixe L, le type du littéral entier est défini comme étant `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md) selon sa taille.  Dans cet exemple, il est de type `long` puisque sa taille est inférieure à la plage définie pour [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Ce suffixe est souvent utilisé lors de l'appel de méthodes surchargées.  Prenez l'exemple suivant de deux méthodes surchargées ayant pour paramètres `long` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 Le recours au suffixe L permet de garantir que le type correct sera appelé, comme indiqué ci\-après :  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 Vous pouvez combiner, au sein d'une expression, le type `long` et d'autres types numériques intégraux, auquel cas le résultat de l'évaluation de l'expression est de type `long` \(ou de type [bool](../../../csharp/language-reference/keywords/bool.md) s'il s'agit d'une expression relationnelle ou booléenne\).  Par exemple, le résultat de l'expression suivante est de type `long` :  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  Vous pouvez également utiliser la lettre minuscule "l" comme suffixe.  Le cas échéant, le compilateur génère un avertissement pour signaler que la lettre "l" peut être confondue avec le chiffre "1". Pour cette raison, préférez le suffixe "L".  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
## Conversions  
 Une conversion implicite prédéfinie intervient de `long` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  Sinon, une conversion explicite doit être utilisée.  Par exemple, l'instruction suivante génère une erreur de compilation si vous ne spécifiez pas de conversion explicite :  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Il y a une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `long`.  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `long`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
  
        long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.Int64>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)