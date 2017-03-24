---
title: "Propri&#233;t&#233;s impl&#233;ment&#233;es automatiquement (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "propriétés implémentées automatiquement (C#)"
  - "propriétés (C#), implémentées automatiquement"
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# Propri&#233;t&#233;s impl&#233;ment&#233;es automatiquement (Guide de programmation&#160;C#)
En C\# 3.0 et versions ultérieures, les propriétés implémentées automatiquement rendent la déclaration de propriété plus concise quand aucune logique supplémentaire n'est requise dans les accesseurs de propriété.  Elles permettent également au code client de créer des objets.  Quand vous déclarez une propriété comme indiqué dans l'exemple suivant, le compilateur crée un champ de stockage privé et anonyme uniquement accessible via les accesseurs `get` et `set` de la propriété.  
  
## Exemple  
 L'exemple suivant montre une classe simple qui a des propriétés implémentées automatiquement :  
  
 [!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 En C\# 6 et versions ultérieures, vous pouvez initialiser des propriétés implémentées automatiquement de la même façon que des champs :  
  
```c#  
public string FirstName { get; set; } = "Jane";  
```  
  
 La classe qui est illustrée dans l'exemple précédent est mutable.  Le code client peut modifier les valeurs dans les objets après leur création.  Dans les classes complexes qui contiennent un comportement significatif \(méthodes\) ainsi que des données, il est souvent nécessaire d'avoir des propriétés publiques.  Toutefois, pour les petites classes ou les petits structs qui encapsulent simplement un ensemble de valeurs \(données\) et qui ont peu de comportements ou aucun, vous devez rendre les objets immuables en déclarant l'accesseur set comme étant [privé](../../../csharp/language-reference/keywords/private.md) \(immuables pour les consommateurs\) ou en déclarant uniquement un accesseur get \(immuables partout sauf dans le constructeur\).  Pour plus d'informations, consultez [Comment : implémenter une classe Lightweight avec des propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Les attributs sont autorisés sur les propriétés implémentées automatiquement, mais évidemment pas sur les champs de stockage puisque ces derniers ne sont pas accessibles à partir de votre code source.  Si vous devez utiliser un attribut sur le champ de stockage d'une propriété, créez simplement une propriété normale.  
  
## Voir aussi  
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)