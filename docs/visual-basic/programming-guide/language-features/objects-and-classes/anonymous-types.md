---
title: "Anonymous Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], about anonymous types"
  - "anonymous types [Visual Basic]"
  - "types [Visual Basic], anonymous"
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
caps.handback.revision: 46
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Anonymous Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Visual Basic prend en charge les types anonymes, qui vous permettent de créer des objets sans écrire de définition de classe pour le type de données.  À la place, le compilateur se charge de générer une classe.  La classe ne possède pas de nom utilisable, hérite directement de <xref:System.Object> et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.  Étant donné que le nom du type de données n'est pas spécifié, ce dernier est dénommé *type anonyme*.  
  
 L'exemple suivant déclare et crée une variable `product` comme instance d'un type anonyme possédant deux propriétés, `Name` et `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 Une *expression de requête* utilise des types anonymes pour associer des colonnes de données sélectionnées par une requête.  Vous ne pouvez pas définir le type du résultat à l'avance, parce que vous ne pouvez pas prédire les colonnes sélectionnées par une requête particulière.  Les types anonymes vous permettent d'écrire une requête qui sélectionne n'importe quel nombre de colonnes, dans n'importe quel ordre.  Le compilateur crée un type de données qui correspond aux propriétés et à l'ordre spécifiés.  
  
 Dans les exemples suivants, `products` est une liste d'objets de produit, possédant chacun de nombreuses propriétés.  La variable `namePriceQuery` contient la définition d'une requête qui, lorsqu'elle est exécutée, retourne une collection d'instances d'un type anonyme possédant deux propriétés, `Name` et `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 La variable `nameQuantityQuery` contient la définition d'une requête qui, lorsqu'elle est exécutée, retourne une collection d'instances d'un type anonyme possédant deux propriétés, `Name` et `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 Pour plus d'informations sur le code créé par le compilateur pour un type anonyme, consultez [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Le nom du type anonyme, généré par le compilateur, peut varier de compilation en compilation.  Votre code ne doit pas utiliser ou reposer sur le nom d'un type anonyme, car ce nom est susceptible de changer lorsqu'un projet est recompilé.  
  
## Déclaration d'un type anonyme  
 La déclaration d'une instance d'un type anonyme utilise une liste d'initialiseurs pour spécifier les propriétés du type.  Vous pouvez spécifier uniquement des propriétés lorsque vous déclarez un type anonyme et pas d'autres éléments de classe tels que les méthodes ou événements.  Dans l'exemples suivant, `product1` est une instance d'un type anonyme possédant deux propriétés : `Name` et `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 Si vous désignez des propriétés comme propriétés de clé, vous pouvez les utiliser pour comparer l'égalité de deux instances de type anonyme.  Toutefois, les valeurs des propriétés de clé ne peuvent pas être modifiées.  Pour plus d'informations, consultez la section Propriétés de clé, plus loin dans cette rubrique.  
  
 Notez que la déclaration d'une instance d'un type anonyme est comparable à la déclaration d'une instance d'un type nommé à l'aide d'un initialiseur d'objet :  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 Pour plus d'informations sur d'autres façons de spécifier des propriétés de type anonymes, consultez [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## Propriétés de clé  
 Les propriétés de clé et les propriétés ne correspondant pas à une clé présentent des différences fondamentales :  
  
-   Seules les valeurs des propriétés de clé sont comparées pour déterminer si deux instances sont égales.  
  
-   Les valeurs des propriétés de clé sont en lecture seule et ne peuvent pas être modifiées.  
  
-   Seules les valeurs des propriétés de clé sont incluses dans l'algorithme de code de hachage généré par le compilateur pour un type anonyme.  
  
### Égalité  
 Les instances de types anonymes sont égales uniquement si elles sont des instances du même type anonyme.  Le compilateur traite deux instances comme instances du même type si elles remplissent les conditions suivantes :  
  
-   Elles sont déclarées dans le même assembly.  
  
-   Leurs propriétés sont déclarées dans le même ordre, avec les mêmes noms et les mêmes types déduits.  Les comparaisons de nom ne respectent pas la casse.  
  
-   Les mêmes propriétés de chaque déclaration sont marquées comme propriétés de clé.  
  
-   Au moins une propriété de chaque déclaration est une propriété de clé.  
  
 Une instance d'un type anonyme qui ne possède pas de propriétés de clé est uniquement égale à elle\-même.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 Deux instances d'un type anonyme identique sont égales si les valeurs de leurs propriétés de clé sont égales.  Les exemples suivants illustrent comment l'égalité est testée.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### Valeurs en lecture seule  
 Les valeurs des propriétés de clé ne peuvent pas être modifiées.  Par exemple, dans `prod8` dans l'exemple précédent, les champs `Name` et `Price` sont en lecture seule dans `read-only`, mais `OnHand` peut être modifié.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## Types anonymes issus d'expressions de requête  
 Les expressions de requête ne requièrent pas toujours la création de types anonymes.  Lorsque cela est possible, ils utilisent un type existant pour contenir les données de colonne.  Cela se produit lorsque la requête retourne des enregistrements entiers de la source de données ou un seul champ de chaque enregistrement.  Dans les exemples de code suivants, `customers` est une collection d'objets d'une classe `Customer`.  La classe possède de nombreuses propriétés et vous pouvez en inclure une ou plusieurs dans le résultat de la requête, dans n'importe quel ordre.  Dans les deux premiers exemples, aucun type anonyme n'est requis parce que les requêtes sélectionnent les éléments de types nommés :  
  
-   `custs1` contient une collection de chaînes, parce que `cust.Name` est une chaîne.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2` contient une collection d'objets `Customer`, parce que chaque élément de `customers` est un objet `Customer` et l'élément entier est sélectionné par la requête.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 Toutefois, les types nommés appropriés ne sont pas toujours disponibles.  Vous pouvez sélectionner des noms de client et des adresses pour un usage particulier, les numéros et les emplacements d'ID de client pour un autre, et noms de client, les adresses et les historiques de commande pour un troisième.  Les types anonymes vous permettent de sélectionner n'importe quelle combinaison de propriétés, dans n'importe quel ordre, sans déclarer d'abord un nouveau type nommé pour contenir le résultat.  À la place, le compilateur crée un type anonyme pour chaque compilation de propriétés.  La requête suivante sélectionne uniquement le nom du client et le numéro d'ID de chaque objet `Customer` dans `customers`.  Par conséquent, le compilateur crée un type anonyme qui contient uniquement ces deux propriétés.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 Les noms et les types de données des propriétés du type anonyme sont transmis des arguments à `Select`, `cust.Name` et `cust.ID`.  Les propriétés d'un type anonyme créé par une requête sont toujours des propriétés de clé.  Lorsque `custs3` est exécuté dans la boucle `For Each` suivante, il en résulte une collection d'instances d'un type anonyme avec deux propriétés de clé, `Name` et `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 Les éléments de la collection représentée par `custs3` sont fortement typés, et vous pouvez utiliser IntelliSense pour parcourir les propriétés disponibles et vérifier leurs types.  
  
 Pour plus d'informations, consultez [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## Choix d'utiliser ou non des types anonymes  
 Avant de créer un objet comme instance d'une classe anonyme, déterminez s'il s'agit de la meilleure option.  Par exemple, si vous souhaitez créer un objet temporaire pour contenir les données connexes, et que vous n'avez pas besoin des autres champs et méthodes qu'une classe complète peut contenir, un type anonyme est une bonne solution.  Les types anonymes sont également pratiques si vous souhaitez une sélection de propriétés différente pour chaque déclaration ou si vous souhaitez modifier l'ordre des propriétés.  Toutefois, si votre projet inclut plusieurs objets possédant les mêmes propriétés, dans un ordre fixe, vous pouvez les déclarer plus facilement en utilisant un type nommé avec un constructeur de classe.  Par exemple, il est plus facile de déclarer plusieurs instances d'une classe `Product` avec un constructeur approprié que de déclarer plusieurs instances d'un type anonyme.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 Un autre avantage des types nommés est que le compilateur peut intercepter une erreur de frappe accidentelle dans un nom de propriété.  Dans les exemples précédents, `firstProd2`, `secondProd2`et `thirdProd2` sont conçus pour être des instances du même type anonyme.  Toutefois, si vous deviez déclarer par erreur `thirdProd2` de l'une des façons suivantes, son type serait différent de celui de `firstProd2` et `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 Plus important encore, il existe des limitations sur l'utilisation de types anonymes qui ne s'appliquent pas aux instances de types nommés.  `firstProd2`, `secondProd2` et `thirdProd2` sont instances du même type anonyme.  Toutefois, le nom du type anonyme partagé n'est pas disponible et ne peut pas figurer à la place d'un nom de type dans votre code.  Par exemple, un type anonyme ne peut pas être utilisé pour définir une signature de méthode, pour déclarer une autre variable ou un autre champ ou dans une déclaration de type.  En conséquence, les types anonymes ne sont pas appropriés lorsque vous devez partager des informations entre les méthodes.  
  
## Définition du type anonyme  
 En réponse à la déclaration d'une instance d'un type anonyme, le compilateur crée une nouvelle définition de classe qui contient les propriétés spécifiées.  
  
 Si le type anonyme contient au moins une propriété de clé, la définition de type substitue trois membres hérités de <xref:System.Object> : <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.ToString%2A>.  Le code produit pour tester l'égalité et déterminer la valeur de code de hachage considère uniquement les propriétés de clé.  Si le type anonyme ne contient pas de propriétés de clé, seul <xref:System.Object.ToString%2A> est substitué.  Les propriétés d'un type anonyme nommées explicitement ne peuvent pas être en conflit avec ces méthodes générées.  Autrement dit, vous ne pouvez pas utiliser `.Equals`, `.GetHashCode` ou `.ToString` pour nommer une propriété.  
  
 Les définitions de type anonymes qui possèdent au moins une propriété de clé implémentent également l'interface <xref:System.IEquatable%601?displayProperty=fullName>, où `T` est le type du type anonyme.  
  
 Pour plus d'informations sur le code créé par le compilateur et les fonctionnalités des méthodes substituées, consultez [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)