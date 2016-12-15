---
title: "Object Initializers: Named and Anonymous Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ObjectInitializer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object initializers [Visual Basic]"
  - "anonymous types [Visual Basic], object initializers"
  - "initializing properties [Visual Basic]"
  - "initializers [Visual Basic]"
  - "named types [Visual Basic]"
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object Initializers: Named and Anonymous Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les initialiseurs d'objets vous permettent de spécifier des propriétés pour un objet complexe, en utilisant une expression unique.  Ils peuvent être utilisés pour créer des instances de types nommés et de types anonymes.  
  
## Déclarations  
 Les déclarations d'instances de types nommés et anonymes peuvent sembler presque identiques, mais leurs effets ne sont pas les mêmes.  Chaque catégorie a ses propres capacités et restrictions.  L'exemple suivant montre une manière pratique de déclarer et d'initialiser une instance de classe nommée, `Customer`, en utilisant une liste d'initialiseurs d'objets.  Remarquez que le nom de la classe est spécifié après le mot clé `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Un type anonyme n'a aucun nom utilisable.  Par conséquent, une instanciation de type anonyme ne peut pas inclure de nom de classe.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Les spécifications et résultats des deux déclarations ne sont pas les mêmes.  Pour `namedCust`, une classe `Customer` ayant une propriété `Name` doit déjà exister, et la déclaration crée une instance de cette classe.  Pour `anonymousCust`, le compilateur définit une nouvelle classe possédant une propriété, une chaîne appelée `Name`, et crée une nouvelle instance de cette classe.  
  
## Types nommés  
 Les initialiseurs d'objets sont un moyen simple d'appeler le constructeur d'un type et de définir ensuite les valeurs de tout ou partie des propriétés, en une instruction unique.  Le compilateur appelle le constructeur approprié pour l'instruction : le constructeur par défaut, si aucun argument n'est présenté, ou un constructeur paramétrable, si un ou plusieurs arguments sont envoyés.  Après cela, les propriétés spécifiées sont initialisées dans l'ordre dans lequel elles sont présentées dans la liste d'initialiseurs.  
  
 Chaque initialisation de la liste d'initialiseurs se compose de l'assignation d'une valeur initiale à un membre de la classe.  Les noms et types de données des membres sont déterminés quand la classe est définie.  Dans les exemples qui suivent, la classe `Customer` doit exister et doit comporter des membres nommés `Name` et `City`, capables d'accepter des valeurs de chaînes.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Vous pouvez également obtenir le même résultat en utilisant le code suivant :  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Chacune de ces déclarations équivaut à l'exemple suivant, qui crée un objet `Customer` en utilisant le constructeur par défaut, puis spécifie des valeurs initiales pour les propriétés `Name` et `City`, en utilisant une instruction `With`.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Si la classe `Customer` contient un constructeur paramétrable qui vous permet d'envoyer une valeur pour `Name`, par exemple, vous pouvez également déclarer et initialiser un objet `Customer` par les méthodes suivantes :  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Vous n'avez pas à initialiser toutes les propriétés, comme le montre code suivant.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 Toutefois, la liste d'initialisation ne peut pas être vide.  Les propriétés non initialisées conservent leurs valeurs par défaut.  
  
### Inférence de type avec les types nommés  
 Vous pouvez raccourcir le code pour la déclaration de `cust1` en combinant des initialiseurs d'objets et l'inférence de type local.  Cela vous permet d'omettre la clause `As` dans la déclaration de variable.  Le type de données de la variable est déduit du type de l'objet créé par l'assignation.  Dans l'exemple suivant, le type de `cust6` est `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### Remarques sur les types nommés  
  
-   Un membre de classe ne peut pas être initialisé plus d'une fois dans la liste d'initialiseurs d'objets.  La déclaration de `cust7` provoque une erreur.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Un membre peut être utilisé pour s'initialiser lui\-même ou initialiser un autre champ.  Si un membre fait l'objet d'un accès avant qu'il n'ait été initialisé, comme dans la déclaration suivante pour `cust8`, la valeur par défaut est utilisée.  Souvenez\-vous que lorsqu'une déclaration qui utilise un initialiseur d'objet est traitée, la première chose qui se passe est que le constructeur approprié est appelé.  Après cela, les champs individuels de la liste d'initialiseurs sont initialisés.  Dans les exemples qui suivent, la valeur par défaut de `Name` est assignée à `cust8`, et une valeur initialisée est assignée en `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     L'exemple suivant utilise le constructeur paramétrable de `cust3` et `cust4` pour déclarer et initialiser `cust10` et `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Les initialiseurs d'objets peuvent être imbriqués.  Dans l'exemple qui suit, `AddressClass` est une classe qui a deux propriétés, `City` et `State`, et la classe `Customer` a une propriété `Address` qui est une instance d' `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   La liste d'initialisation ne peut pas être vide.  
  
-   L'instance initialisée ne peut pas être de type Objet.  
  
-   Les membres d'une classe en cours d'initialisation ne peuvent pas être des membres partagés, des membres en lecture seule, des constantes ni des appels de méthode.  
  
-   Les membres de classes en cours d'initialisation ne peuvent être ni indexés ni qualifiés.  Les exemples suivants déclenchent des erreurs du compilateur :  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## Types anonymes  
 Les types anonymes utilisent les initialiseurs d'objets pour créer des instances de types nouveaux que vous ne définissez ni ne nommez explicitement.  Au contraire, le compilateur génère un type d'après les propriétés que vous désignez, dans la liste d'initialiseurs d'objets.  Le nom du type de données n'étant pas spécifié, ce dernier est considéré comme un *type anonyme*.  Comparez, par exemple, la déclaration suivante à la déclaration préalable correspondant à `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 La seule différence est syntaxique : aucun nom n'est spécifié après `New` pour le type de données.  Toutefois, ce qui se passe est assez différent.  Le compilateur définit un nouveau type anonyme qui a deux propriétés, `Name` et `City`et crée une instance de ce type avec les valeurs spécifiées.  L'inférence de type détermine les types `Name` et `City` de l'exemple comme étant des chaînes.  
  
> [!CAUTION]
>  Le nom du type anonyme, généré par le compilateur, et peut varier de compilation en compilation.  Votre code ne doit pas utiliser ni compter sur le nom d'un type anonyme.  
  
 Le nom du type n'étant pas disponible, vous ne pouvez pas utiliser de clause `As` pour déclarer `cust13`.  Son type doit être déduit.  Sans utiliser la liaison tardive, cela limite l'utilisation de types anonymes aux variables locales.  
  
 Les types anonymes fournissent un support essentiel aux requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Pour plus d'informations sur l'utilisation des types anonymes dans les requêtes, consultez [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) et [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### Remarques sur les types anonymes  
  
-   En général, la plupart ou la totalité des propriétés d'une déclaration de type anonyme est constituée de propriétés de clé, indiquées en tapant le mot clé `Key` devant le nom de la propriété.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Pour plus d'informations sur les propriétés de clé, consultez [Key](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   À l'instar des types nommés, les listes d'initialiseurs pour les définitions de types anonymes doivent déclarer au moins une propriété.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Lorsqu'une instance de type anonyme est déclarée, le compilateur génère une définition de type anonyme correspondante.  Les noms et types de données des propriétés sont pris à la déclaration d'instance et sont inclus par le compilateur dans la définition.  Les propriétés ne sont pas nommées ni définies en avance, comme elles seraient dans le cas d'un type nommé.  Leurs types sont déduits.  Vous ne pouvez pas spécifier les types de données des propriétés en utilisant une clause `As`.  
  
-   Les types anonymes peuvent également établir les noms et valeurs de leurs propriétés de nombreuses manières différentes.  Par exemple, une propriété de type anonyme peut prendre à la fois le nom et la valeur d'une variable, ou le nom et la valeur de la propriété d'un autre objet.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Pour plus d'informations sur les options de définition des propriétés dans les types anonymes, consultez [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## Voir aussi  
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)   
 [How to: Declare an Object by Using an Object Initializer](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)