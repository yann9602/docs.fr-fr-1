---
title: "How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "collection initializers [Visual Basic]"
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous utilisez un initialiseur de collection pour créer une collection, le compilateur de Visual Basic recherche une méthode `Add` du type de collection pour lequel les paramètres de la méthode `Add` correspondent aux types des valeurs dans l'initialiseur de collection.  Cette méthode `Add` est utilisée pour remplir la collection avec les valeurs de l'initialiseur de collection.  
  
 Si aucune méthode `Add` correspondante n'existe et que vous ne pouvez pas modifier le code de la collection, vous pouvez ajouter une méthode d'extension appelée `Add` qui prend les paramètres requis par l'initialiseur de collection.  Il s'agit de la technique généralement employée lorsque vous utilisez des initialiseurs de collection pour des collections génériques.  
  
## Exemple  
 L'exemple suivant indique comment ajouter une méthode d'extension au type <xref:System.Collections.Generic.List%601> générique afin qu'un initialiseur de collection puisse être utilisé pour ajouter des objets de type `Employee`.  La méthode d'extension vous permet d'utiliser la syntaxe raccourcie de l'initialiseur de collection.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/visualbasic/how-to-create-an-add-ext_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/visualbasic/how-to-create-an-add-ext_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/visualbasic/how-to-create-an-add-ext_3.vb)]  
  
## Voir aussi  
 [Collection Initializers](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)