---
title: "enum (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "enum"
  - "enum_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "enum (mot clé C#)"
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 36
---
# enum (r&#233;f&#233;rence C#)
Le mot clé `enum` est utilisé pour déclarer une énumération. Il s’agit d’un type distinct qui se compose d’un ensemble de constantes nommées, appelé liste d’énumérateurs.  
  
 Il est généralement préférable de définir une énumération directement dans un espace de noms pour que toutes les classes de l’espace de noms puissent y accéder avec la même facilité. Toutefois, une énumération peut également être imbriquée dans une classe ou un struct.  
  
 Par défaut, le premier énumérateur a la valeur 0 et chaque énumérateur successif est augmenté de 1. Par exemple, dans l’énumération suivante, `Sat` est `0`, `Sun` est `1`, `Mon` est `2`, et ainsi de suite.  
  
```  
  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Les énumérateurs peuvent utiliser des initialiseurs pour remplacer les valeurs par défaut, comme illustré dans l’exemple suivant.  
  
```  
  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Dans cette énumération, le début de la séquence des éléments est forcé à `1` au lieu de `0`. Il est cependant recommandé d’inclure une constante qui a la valeur 0. Pour plus d'informations, consultez [Types énumération](../../../csharp/programming-guide/enumeration-types.md).  
  
 Chaque type énumération a un type sous\-jacent, ce qui peut être tout type intégral, sauf [char](../../../csharp/language-reference/keywords/char.md). Le type sous\-jacent par défaut des éléments de l’énumération est [int](../../../csharp/language-reference/keywords/int.md). Pour déclarer une énumération d’un autre type intégral, comme [byte](../../../csharp/language-reference/keywords/byte.md), utilisez un signe deux\-points après l’identificateur, suivi du type, comme illustré dans l’exemple suivant.  
  
```  
  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Les types approuvés pour une énumération sont `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [court](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Une variable de type `Days` peut être affectée de n’importe quelle valeur dans la plage du type sous\-jacent ; les valeurs ne sont pas limitées aux constantes nommées.  
  
 La valeur par défaut de `enum E` est la valeur produite par l’expression `(E)0`.  
  
> [!NOTE]
>  Le nom d’un énumérateur ne peut pas contenir d’espaces.  
  
 Le type sous\-jacent spécifie la quantité de stockage allouée pour chaque énumérateur. Cependant, un cast explicite est nécessaire pour convertir du type `enum` en un type intégral. Par exemple, l’instruction suivante affecte l’énumérateur `Sun` à une variable du type [int](../../../csharp/language-reference/keywords/int.md) en utilisant un cast pour convertir de `enum` en `int`.  
  
```  
  
int x = (int)Days.Sun;  
```  
  
 Quand vous appliquez <xref:System.FlagsAttribute?displayProperty=fullName> à une énumération qui contient des éléments qui peuvent être combinés avec une opération `OR` au niveau du bit, l’attribut affecte le comportement d’`enum` quand elle est utilisée avec certains outils. Vous pouvez remarquer ces modifications quand vous utilisez des outils comme les méthodes de la classe <xref:System.Console> et l’évaluateur d’expression. \(Voir le troisième exemple.\)  
  
## Programmation fiable  
 Tout comme avec n’importe quelle constante, toutes les références aux valeurs individuelles d’une énumération sont converties en littéraux numériques au moment de la compilation. Cette opération peut créer des problèmes potentiels de gestion de version, comme décrit dans [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
 L’affectation de valeurs supplémentaires à de nouvelles versions d’énumérations ou la modification des valeurs des membres d’une énumération dans une nouvelle version peut entraîner des problèmes pour le code source dépendant. Les valeurs des énumérations sont souvent utilisées dans des instructions [switch](../../../csharp/language-reference/keywords/switch.md). Si des éléments supplémentaires ont été ajoutées au type `enum`, la section par défaut de l’instruction switch peut être sélectionnée de façon inattendue.  
  
 Si d’autres développeurs utilisent votre code, vous devez fournir des instructions sur la manière dont leur code doit réagir si de nouveaux éléments sont ajoutés à des types `enum`.  
  
## Exemple  
 Dans l’exemple suivant, une énumération, `Days`, est déclarée. Deux énumérateurs sont explicitement convertis en entiers et affectés à des variables entières.  
  
 [!code-cs[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/csharp/enum_1.cs)]  
  
## Exemple  
 Dans l’exemple suivant, l’option de type de base est utilisée pour déclarer une `enum` dont les membres sont de type `long`. Notez que même si le type sous\-jacent de l’énumération est `long`, les membres de l’énumération doivent toujours être explicitement convertis en type `long` en utilisant un cast.  
  
 [!code-cs[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/csharp/enum_2.cs)]  
  
## Exemple  
 L’exemple de code suivant montre l’utilisation et l’effet de l’attribut <xref:System.FlagsAttribute?displayProperty=fullName> sur une déclaration `enum`.  
  
 [!code-cs[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/csharp/enum_3.cs)]  
  
## Commentaires  
 Si vous supprimez `Flags`, l’exemple affiche les valeurs suivantes :  
  
 `5`  
  
 `5`  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Types énumération](../../../csharp/programming-guide/enumeration-types.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)