---
title: "Propri&#233;t&#233;s (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.properties"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, propriétés"
  - "propriétés (C#)"
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 38
---
# Propri&#233;t&#233;s (Guide de programmation C#)
Une propriété est un membre qui fournit un mécanisme flexible pour la lecture, l'écriture ou le calcul de la valeur d'un champ privé.  Les propriétés peuvent être utilisées comme s'il s'agissaient de membres de données publics, mais il s'agit en fait de méthodes spéciales appelées *accesseurs*.  Elles permettent aux données d'être facilement accessibles tout en soutenant quand même la sécurité et la flexibilité des méthodes.  
  
 Dans cet exemple, la classe `TimePeriod` stocke une période.  La classe stocke en interne la durée en secondes, mais une propriété nommée `Hours` permet à un client de spécifier une durée en heures.  Les accesseurs de la propriété `Hours` effectuent la conversion entre heures et secondes.  
  
## Exemple  
 [!code-cs[csProgGuideProperties#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/properties_1.cs)]  
  
## Définitions de corps d'expression  
 Il est courant d'avoir des propriétés qui se contentent de retourner immédiatement le résultat d'une expression.  Il existe un raccourci de syntaxe pour définir ces propriétés à l'aide de `=>` :  
  
```c#  
public string Name => First + " " + Last;   
```  
  
 La propriété doit être en lecture seule et vous n'utilisez pas le mot clé d'accesseur `get`.  
  
## Vue d'ensemble des propriétés  
  
-   Les propriétés permettent à une classe d'exposer un moyen public d'obtenir et de définir des valeurs, tout en masquant le code d'implémentation ou de vérification.  
  
-   Un accesseur de propriété [get](../../../csharp/language-reference/keywords/get.md) est utilisé pour retourner la valeur de la propriété et un accesseur [set](../../../csharp/language-reference/keywords/set.md) est utilisé pour affecter une nouvelle valeur.  Ces accesseurs peuvent avoir différents niveaux d'accès.  Pour plus d'informations, consultez [Restriction d'accessibilité de l'accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
-   Le mot clé [value](../../../csharp/language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l'accesseur `set`.  
  
-   Les propriétés qui n'implémentent pas un accesseur `set` sont en lecture seule.  
  
-   Pour les propriétés simples qui ne requièrent aucun code d'accesseur personnalisé, envisagez la possibilité d'utiliser des propriétés implémentées automatiquement.  Pour plus d'informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## Rubriques connexes  
  
-   [Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Propriétés d'interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Comparaison entre propriétés et indexeurs](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Restriction d'accessibilité de l'accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)