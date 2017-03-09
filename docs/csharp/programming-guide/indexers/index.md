---
title: "Indexeurs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.indexers"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, indexeurs"
  - "indexeurs (C#)"
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# Indexeurs (Guide de programmation C#)
Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux.  Les indexeurs s'apparentent aux [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) à l'exception près que leurs accesseurs acceptent des paramètres.  
  
 Dans l'exemple suivant, une classe générique est définie et fournie avec des méthodes d'accesseur [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) simples en tant que moyen d'affecter et de récupérer des valeurs.  La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.  
  
 [!code-cs[csProgGuideIndexers#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/index_1.cs)]  
  
> [!NOTE]
>  Pour plus d'exemples, consultez [Rubriques connexes](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## Définitions de corps d'expression  
 Il est courant d'avoir des indexeurs qui se contentent de retourner immédiatement le résultat d'une expression.  Il existe un raccourci de syntaxe pour définir les indexeurs à l'aide de `=>` :  
  
```c#  
public Customer this[long id] => store.LookupCustomer(id);  
  
```  
  
 L'indexeur doit être en lecture seule et vous n'utilisez pas le mot clé d'accesseur `get`.  
  
## Vue d'ensemble des indexeurs  
  
-   Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.  
  
-   Un accesseur `get` retourne une valeur.  Un accesseur `set` affecte une valeur.  
  
-   Le mot clé [this](../../../csharp/language-reference/keywords/this.md) est utilisé pour définir les indexeurs.  
  
-   Le mot clé [value](../../../csharp/language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l'indexeur `set`.  
  
-   Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.  
  
-   Les indexeurs peuvent être surchargés.  
  
-   Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.  
  
##  <a name="BKMK_RelatedSections"></a> Rubriques connexes  
  
-   [Utilisation d'indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Indexeurs dans les interfaces](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Comparaison entre propriétés et indexeurs](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Restriction d'accessibilité de l'accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)