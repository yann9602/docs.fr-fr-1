---
title: "Utilisation d&#39;op&#233;rateurs de conversion (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "opérateurs de conversion (C#)"
  - "conversions (C#), opérateurs"
  - "opérateurs de conversion explicite (C#)"
  - "opérateurs de conversion implicite (C#)"
  - "opérateurs (C#), conversion"
  - "conversions définies par l'utilisateur (C#)"
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Utilisation d&#39;op&#233;rateurs de conversion (Guide de programmation&#160;C#)
Il est possible d'utiliser les opérateurs de conversion `implicit`, qui sont plus faciles à utiliser, ou les opérateurs de conversion `explicit`, qui indiquent clairement à tout personne lisant le code que l'on convertit un type.  Cette rubrique illustre les deux types d'opérateurs de conversion.  
  
> [!NOTE]
>  Pour plus d'informations sur les conversions de types simples, consultez [Comment : convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Comment : convertir un tableau de byte en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Comment : effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), ou <xref:System.Convert>.  
  
## Exemple  
 Voici un exemple d'opérateur de conversion explicite.  Cet opérateur convertit le type <xref:System.Byte> en un type valeur appelé `Digit`.  Tous les octets ne pouvant pas être convertis en un chiffre, la conversion est explicite, ce qui signifie qu'un cast doit être utilisé, comme illustré dans la méthode `Main`.  
  
 [!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-conversion-operators_1.cs)]  
  
## Exemple  
 Cet exemple montre un opérateur de conversion implicite en définissant un opérateur de conversion qui annule ce que l'exemple antérieur a fait : il convertit d'une classe de valeur appelée `Digit` en type <xref:System.Byte> intégral.  Tout chiffre pouvant être converti en un <xref:System.Byte>, il n'y a aucun besoin de forcer les utilisateurs à être explicites à propos de la conversion.  
  
 [!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-conversion-operators_2.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Conversion, opérateurs](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [is](../../../csharp/language-reference/keywords/is.md)