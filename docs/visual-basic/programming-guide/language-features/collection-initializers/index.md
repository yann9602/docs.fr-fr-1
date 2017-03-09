---
title: "Collection Initializers (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.CollectionInitializer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "collection initializers [Visual Basic]"
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Collection Initializers (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les *initialiseurs de collection* fournissent une syntaxe raccourcie qui vous permet de créer une collection et de la remplir avec un ensemble initial de valeurs.  Les initialiseurs de collection sont utiles lorsque vous créez une collection à partir d'un jeu de valeurs connues, par exemple, une liste d'options de menu ou de catégories, un jeu initial de valeurs numériques, une liste statique de chaînes telles que les jours ou les mois, ou des emplacements géographiques tels qu'une liste d'états utilisée pour la validation.  
  
 Pour plus d'informations sur les collections, consultez [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Vous identifiez un initialiseur de collection à l'aide du mot clé `From` suivi des accolades \(`{}`\).  Cela s'apparente à la syntaxe de littéral de tableau décrite dans [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  Les exemples suivants montrent les différentes façons d'utiliser les initialiseurs de collection pour la création de collections.  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_1.vb)]  
  
> [!NOTE]
>  C\# fournit également des initialiseurs de collection.  Les initialiseurs de collection de C\# fournissent les mêmes fonctionnalités que les initialiseurs de collection de Visual Basic.  Pour plus d'informations sur les initialiseurs de collection C\#, consultez [Initialiseurs d'objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## Syntaxe  
 Un initialiseur de collection se compose d'une liste de valeurs séparées par des virgules placées entre accolades \(`{}`\), précédée par le mot clé `From`, comme indiqué dans le code suivant.  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_2.vb)]  
  
 Lorsque vous créez une collection, telle qu'un <xref:System.Collections.Generic.List%601> ou un <xref:System.Collections.Generic.Dictionary%602>, vous devez fournir le type de collection avant l'initialiseur de collection, comme indiqué dans le code suivant.  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_3.vb)]  
  
> [!NOTE]
>  Vous ne pouvez pas combiner un initialiseur de collection et un initialiseur d'objet pour initialiser le même objet de collection.  Vous pouvez utiliser des initialiseurs d'objets pour initialiser des objets dans un initialiseur de collection.  
  
## Création d'une collection à l'aide d'un initialiseur de collection  
 Lorsque vous créez une collection à l'aide d'un initialiseur de collection, chaque valeur fournie dans l'initialiseur de collection est passée à la méthode `Add` appropriée de la collection.  Par exemple, si vous créez un <xref:System.Collections.Generic.List%601> à l'aide d'un initialiseur de collection, chaque valeur de chaîne dans l'initialiseur de collection est passée à la méthode <xref:System.Collections.Generic.List%601.Add%2A>.  Si vous souhaitez créer une collection à l'aide d'un initialiseur de collection, le type spécifié doit être un type de collection valide.  Les types de collection valides incluent notamment les classes qui implémentent l'interface <xref:System.Collections.Generic.IEnumerable%601> ou héritent de la classe <xref:System.Collections.CollectionBase>.  Le type spécifié doit également exposer une méthode `Add` qui répond aux critères suivants.  
  
-   La méthode `Add` doit être disponible à partir de la portée dans laquelle l'initialiseur de collection est appelé.  La méthode `Add` ne doit pas obligatoirement être publique si vous utilisez l'initialiseur de collection dans un scénario où les méthodes non publiques de la collection sont accessibles.  
  
-   La méthode `Add` doit être un membre d'instance ou un membre `Shared` de la classe de collection, ou une méthode d'extension.  
  
-   Il doit exister une méthode `Add` qui peut être mise en correspondance, selon les règles de résolution de surcharge, avec les types fournis dans l'initialiseur de collection.  
  
 L'exemple de code suivant indique comment créer une collection `List(Of Customer)` à l'aide d'un initialiseur de collection.  Lorsque le code est exécuté, chaque objet `Customer` est passé à la méthode `Add(Customer)` de la liste générique.  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_4.vb)]  
  
 L'exemple de code suivant illustre un code équivalent qui n'utilise pas d'initialiseur de collection.  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_5.vb)]  
  
 Si la collection inclut une méthode `Add` dont les paramètres correspondent au constructeur pour l'objet `Customer`, vous pouvez imbriquer des valeurs de paramètre pour la méthode `Add` dans des initialiseurs de collection, comme décrit dans la section suivante.  Si la collection n'a pas de méthode `Add`, vous pouvez en créer une comme méthode d'extension.  Pour obtenir un exemple de création de méthode `Add` comme méthode d'extension pour une collection, consultez [How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md).  Pour obtenir un exemple de création d'une collection personnalisée qui peut être utilisée avec un initialiseur de collection, consultez [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).  
  
## Imbrication d'initialiseurs de collection  
 Vous pouvez imbriquer des valeurs dans un initialiseur de collection pour identifier une surcharge spécifique d'une méthode `Add` pour la collection créée.  Les valeurs passées à la méthode `Add` doivent être séparées par des virgules et placées entre accolades \(`{}`\), comme dans un littéral de tableau ou un initialiseur de collection.  
  
 Lorsque vous créez une collection à l'aide de valeurs imbriquées, chaque élément de la liste de valeurs imbriquée est passé comme argument à la méthode `Add` qui correspond aux types d'élément.  L'exemple de code suivant crée un <xref:System.Collections.Generic.Dictionary%602> dans lequel les clés sont de type `Integer` et les valeurs de type `String`.  Chacune des listes de valeurs imbriquées est mise en correspondance avec la méthode <xref:System.Collections.Generic.Dictionary%602.Add%2A> pour le `Dictionary`.  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_6.vb)]  
  
 L'exemple de code précédent équivaut au code suivant.  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/visualbasic/index_7.vb)]  
  
 Seules les listes de valeurs imbriquées du premier niveau de l'imbrication sont envoyées à la méthode `Add` pour le type de collection.  Les niveaux plus profonds de l'imbrication sont traités comme littéraux de tableaux et les listes de valeurs imbriquées ne sont pas mises en correspondance avec la méthode `Add` des collections.  
  
## Rubriques connexes  
  
|||  
|-|-|  
|Titre|Description|  
|[How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Montre comment créer une méthode d'extension appelée `Add` qui peut être utilisé pour remplir une collection avec les valeurs d'un initialiseur de collection.|  
|[How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|montre comment activer l'utilisation d'un initialiseur de collection en incluant une méthode d' `Add` dans une classe de collection qui implémente `IEnumerable`.|  
  
## Voir aussi  
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Auto\-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)