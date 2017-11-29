---
title: "Initialiseurs d'objets : types nommés et anonymes (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 349e4f7b4902eb18845fee7cb4d01b217849a4d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Initialiseurs d'objets : types nommés et anonymes (Visual Basic)
Initialiseurs d’objets vous permettent de vous permet de spécifier les propriétés d’un objet complexe à l’aide d’une expression unique. Ils peuvent être utilisés pour créer des instances de types nommés et de types anonymes.  
  
## <a name="declarations"></a>Déclarations  
 Déclarations d’instances de types nommés et anonymes peuvent sembler presque identiques, mais leurs effets ne sont pas identiques. Chaque catégorie dispose de capacités et les restrictions qui lui sont propres. L’exemple suivant montre un moyen pratique pour déclarer et initialiser une instance d’une classe nommée, `Customer`, à l’aide d’une liste d’initialiseurs objet. Notez que le nom de la classe est spécifié après le mot clé `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Un type anonyme n’a pas de nom utilisable. Par conséquent, une instanciation d’un type anonyme ne peut pas inclure un nom de classe.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 La configuration requise et les résultats des deux déclarations ne sont pas identiques. Pour `namedCust`, un `Customer` classe qui a un `Name` propriété doit déjà exister, et la déclaration crée une instance de cette classe. Pour `anonymousCust`, le compilateur définit une nouvelle classe qui possède une propriété, une chaîne appelée `Name`et crée une nouvelle instance de cette classe.  
  
## <a name="named-types"></a>Types nommés  
 Initialiseurs d’objets fournissent un moyen simple pour appeler le constructeur d’un type, puis définissez les valeurs de certaines ou toutes les propriétés dans une instruction unique. Le compilateur appelle le constructeur approprié pour l’instruction : le constructeur par défaut si aucun argument n’est présentés, ou un constructeur paramétrable, si un ou plusieurs arguments sont envoyé. Après cela, les propriétés spécifiées sont initialisées dans l’ordre dans lequel elles sont présentées dans la liste d’initialiseurs.  
  
 Chaque initialisation de la liste d’initialiseurs se compose de l’attribution d’une valeur initiale à un membre de la classe. Les noms et types de données des membres sont déterminées lors de la classe est définie. Dans les exemples suivants, le `Customer` classe doit exister et doivent comporter des membres nommés `Name` et `City` qui peut accepter des valeurs de chaîne.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Vous pouvez également obtenir le même résultat en utilisant le code suivant :  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Chacune de ces déclarations est équivalente à l’exemple suivant, qui crée un `Customer` de l’objet à l’aide du constructeur par défaut, puis spécifie des valeurs initiales pour les `Name` et `City` propriétés à l’aide un `With` instruction.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Si le `Customer` classe contient un constructeur paramétrable qui vous permet d’envoyer une valeur pour `Name`, par exemple, vous pouvez également déclarer et initialiser un `Customer` objet comme suit :  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Il est inutile d’initialiser toutes les propriétés, comme le montre le code suivant.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 Toutefois, la liste d’initialisation ne peut pas être vide. Propriétés non initialisées conservent leurs valeurs par défaut.  
  
### <a name="type-inference-with-named-types"></a>Inférence de type avec des Types nommés  
 Vous pouvez raccourcir le code pour la déclaration de `cust1` en combinant des initialiseurs d’objets et l’inférence de type local. Cela vous permet d’omettre le `As` clause dans la déclaration de variable. Le type de données de la variable est déduit du type de l’objet qui est créé par l’assignation. Dans l’exemple suivant, le type de `cust6` est `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Remarques sur les Types nommés  
  
-   Un membre de classe ne peut pas être initialisé plusieurs fois dans la liste d’initialiseurs objet. La déclaration de `cust7` provoque une erreur.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Un membre peut être permettant d’initialiser lui-même ou un autre champ. Si un membre est accessible avant qu’il a été initialisé, comme dans la déclaration suivante pour `cust8`, la valeur par défaut sera utilisée. N’oubliez pas que lorsqu’une déclaration qui utilise un initialiseur d’objet est traitée, la première chose qui se produit est que le constructeur approprié est appelé. Après cela, les champs individuels dans la liste d’initialiseurs sont initialisés. Dans les exemples suivants, la valeur par défaut `Name` est attribué pour `cust8`, et une valeur initialisée est assignée dans `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     L’exemple suivant utilise le constructeur paramétrable de `cust3` et `cust4` pour déclarer et initialiser `cust10` et `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Initialiseurs d’objets peuvent être imbriquées. Dans l’exemple suivant, `AddressClass` est une classe qui a deux propriétés, `City` et `State`et le `Customer` classe a un `Address` propriété qui est une instance de `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   La liste d’initialisation ne peut pas être vide.  
  
-   L’instance en cours d’initialisation ne peut pas être de type Object.  
  
-   Membres de classe en cours d’initialisation ne peut pas être des membres partagés, des membres en lecture seule, des constantes ou des appels de méthode.  
  
-   Membres de classe en cours d’initialisation ne peut pas être qualifiés ou indexés. Les exemples suivants déclenchent des erreurs du compilateur :  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Types anonymes  
 Les types anonymes utilisent les initialiseurs d’objets pour créer des instances de nouveaux types que vous ne définissez pas explicitement et du nom. Au lieu de cela, le compilateur génère un type en fonction des propriétés que vous désignez dans la liste d’initialiseurs objet. Étant donné que le nom du type n’est pas spécifié, il est appelé un *type anonyme*. Par exemple, comparer la déclaration suivante au précédent pour `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 La seule différence est syntaxique : aucun nom n’est spécifié après `New` pour le type de données. Toutefois, il est très différente de ce qui se passe. Le compilateur définit un nouveau type anonyme qui a deux propriétés, `Name` et `City`et crée une instance de celui-ci avec les valeurs spécifiées. L’inférence de type détermine les types de `Name` et `City` dans l’exemple pour être des chaînes.  
  
> [!CAUTION]
>  Le nom du type anonyme est généré par le compilateur et peut varier de compilation en compilation. Votre code ne doit pas utiliser ou s’appuient sur le nom d’un type anonyme.  
  
 Le nom du type n’est pas disponible, vous ne pouvez pas utiliser un `As` clause pour déclarer `cust13`. Son type doit être déduit. Sans utiliser de liaison tardive, ce qui limite l’utilisation de types anonymes aux variables locales.  
  
 Types anonymes ne fournissent une prise en charge critique pour [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] des requêtes. Pour plus d’informations sur l’utilisation de types anonymes dans les requêtes, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) et [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Remarques sur les Types anonymes  
  
-   En règle générale, tout ou partie des propriétés dans une déclaration de type anonyme seront des propriétés de clé, qui sont indiquées en tapant le mot clé `Key` devant le nom de propriété.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Pour plus d’informations sur les propriétés de clé, consultez [clé](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Comme types nommés, les listes d’initialiseurs pour les définitions de type anonymes doivent déclarer au moins une propriété.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Lorsqu’une instance d’un type anonyme est déclarée, le compilateur génère une définition de type anonyme correspondante. Les noms et types de données des propriétés sont tirées de la déclaration d’instance et sont inclus par le compilateur dans la définition. Les propriétés ne sont pas nommées et définies à l’avance, tels qu’ils seraient pour un type nommé. Leurs types sont déduits. Vous ne pouvez pas spécifier les types de données des propriétés en utilisant un `As` clause.  
  
-   Les types anonymes peuvent également établir les noms et valeurs de leurs propriétés de plusieurs autres façons. Par exemple, une propriété de type anonyme peut prendre le nom et la valeur d’une variable, ou le nom et la valeur d’une propriété d’un autre objet.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Pour plus d’informations sur les options permettant de définir des propriétés dans les types anonymes, consultez [Comment : déduire les noms de propriétés et les Types dans les déclarations de Type anonyme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Guide pratique : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)  
 [Guide pratique : déclarer un objet à l’aide d’un initialiseur d’objet](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
