---
title: "Opérateurs conditionnels Null (C# et Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a>Opérateurs conditionnels Null (C# et Visual Basic)
Ces opérateurs sont utilisés pour rechercher les valeurs Null avant d'effectuer une opération d'accès au membre (`?.`) ou d'indexation (`?[`).  Ils permettent d'écrire moins de code pour gérer les vérifications Null, notamment pour l'exploration des structures de données.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 Le dernier exemple montre que les opérateurs conditionnels Null ont un effet de court-circuit.  Si une opération dans une chaîne d'opérations d'accès au membre et d'indexation conditionnelles retourne une valeur Null, l'exécution du reste de la chaîne s'arrête.  Les autres opérations ayant une priorité moins élevée dans l'expression continuent.  Dans l’exemple ci-dessous, `E` s’exécute à la seconde ligne, et les opérations `??` et `==` sont exécutées.  Dans la première ligne, `??` court-circuite et `E` ne s’exécute pas quand la partie gauche à une valeur non null.
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 L'accès au membre conditionnel Null s'utilise également pour appeler des délégués de façon thread-safe, avec beaucoup moins de code.  Avec l'ancienne méthode, vous deviez utiliser un code similaire au suivant :  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 La nouvelle méthode est beaucoup plus simple :  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 La nouvelle méthode est thread-safe, car le compilateur génère du code qui évalue `PropertyChanged` une seule fois, en conservant le résultat dans une variable temporaire.  
  
 Vous devez explicitement appeler la méthode `Invoke`, car il n'existe pas de syntaxe d'appel de délégué conditionnel Null `PropertyChanged?(e)`.  Il y avait trop de situations d'analyse ambiguës pour pouvoir utiliser une telle syntaxe.  
  
## <a name="language-specifications"></a>Spécifications du langage  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Pour plus d’informations, consultez [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 [?? (opérateur de fusion null)](null-conditional-operator.md)  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)
