---
title: Indexeurs (Guide de programmation C#)
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 784308f3073114cd0c07cf15edae527a2654edec
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="indexers-c-programming-guide"></a>Indexeurs (Guide de programmation C#)

Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux. La valeur indexée peut être définie ou récupérée sans spécifier explicitement un membre de type ou d’instance. Les indexeurs s’apparentent aux [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) à l’exception près que leurs accesseurs acceptent des paramètres.  
 
 L’exemple suivant définit une classe générique avec des méthodes d’accesseur [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) simples pour attribuer et récupérer des valeurs. La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.  
  
 [!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Pour plus d’exemples, consultez [Rubriques connexes](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Définitions de corps d'expression  
 
Il est courant pour l’accesseur get ou set d’un indexeur d’être constitué d’une instruction unique qui retourne ou définit une valeur. Les membres expression-bodied fournissent une syntaxe simplifiée pour prendre en charge ce scénario. À partir de C# 6, un indexeur en lecture seule peut être implémenté comme un membre expression-bodied, comme le montre l’exemple suivant.

[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Notez que `=>` introduit le corps de l’expression et que le mot clé `get` n’est pas utilisé. 

À partir de C# 7, l’accesseur get et l’accesseur set peuvent être implémentés en tant que membres expression-bodied. Dans ce cas, les deux mots clés `get` et `set` doivent être utilisés. Exemple :

[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Vue d'ensemble des indexeurs  
  
-   Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.  
  
-   Un accesseur `get` retourne une valeur. Un accesseur `set` affecte une valeur.  
  
-   Le mot clé [this](../../../csharp/language-reference/keywords/this.md) est utilisé pour définir l’indexeur.  
  
-   Le mot clé [value](../../../csharp/language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l’indexeur `set`.  
  
-   Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.  
  
-   Les indexeurs peuvent être surchargés.  
  
-   Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.  
  
##  <a name="BKMK_RelatedSections"></a> Rubriques connexes  
  
-   [Utilisation d’indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Indexeurs dans les interfaces](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Comparaison entre propriétés et indexeurs](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Restriction d’accessibilité de l’accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)

