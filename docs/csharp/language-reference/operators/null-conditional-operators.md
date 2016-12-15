---
title: "Op&#233;rateurs conditionnels Null (C# et Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Op&#233;rateurs conditionnels Null (C# et Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ces opérateurs sont utilisés pour rechercher les valeurs Null avant d'effectuer une opération d'accès au membre \(`?.`\) ou d'indexation \(`?[`\).  Ils permettent d'écrire moins de code pour gérer les vérifications Null, notamment pour l'exploration des structures de données.  
  
```c#  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
```vb  
Dim length = customers?.Length  ‘’ null if customers is null  
Dim first as Customer = customers?(0);  ‘’ null if customers is null  
Dim count as Integer? = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
 Le dernier exemple montre que les opérateurs conditionnels Null ont un effet de court\-circuit.  Si une opération dans une chaîne d'opérations d'accès au membre et d'indexation conditionnelles retourne une valeur Null, l'exécution du reste de la chaîne s'arrête.  Les autres opérations ayant une priorité moins élevée dans l'expression continuent.  Dans l'exemple ci\-dessous, `E` s'exécute toujours, et les opérations `??` et `==` sont exécutées.  
  
```vb-c#  
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
  
```  
  
 L'accès au membre conditionnel Null s'utilise également pour appeler des délégués de façon thread\-safe, avec beaucoup moins de code.  Avec l'ancienne méthode, vous deviez utiliser un code similaire au suivant :  
  
```c#  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…)  
  
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
  
```  
  
 La nouvelle méthode est beaucoup plus simple :  
  
```vb-c#  
PropertyChanged?.Invoke(e)  
  
```  
  
 La nouvelle méthode est thread\-safe, car le compilateur génère du code qui évalue `PropertyChanged` une seule fois, en conservant le résultat dans une variable temporaire.  
  
 Vous devez explicitement appeler la méthode `Invoke`, car il n'existe pas de syntaxe d'appel de délégué conditionnel Null `PropertyChanged?(e)`.  Il y avait trop de situations d'analyse ambiguës pour pouvoir utiliser une telle syntaxe.  
  
## Spécifications du langage  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 Pour plus d'informations, voir [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)