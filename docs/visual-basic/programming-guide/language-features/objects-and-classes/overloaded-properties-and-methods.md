---
title: "Overloaded Properties and Methods (Visual Basic) | Microsoft Docs"
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
  - "properties [Visual Basic], overloading"
  - "methods [Visual Basic], overloading"
  - "shadowing"
  - "names, multiple procedures with same"
  - "procedures, mulltiples with same name"
  - "classes [Visual Basic], properties"
  - "classes [Visual Basic], methods"
  - "method overloading"
  - "Overloads keyword, overloaded members"
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Overloaded Properties and Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La surcharge consiste à créer plusieurs procédures, constructeurs d'instance ou propriétés dans une classe avec le même nom, mais avec des types d'argument différents.  
  
## Utilisation de la surcharge  
 La surcharge est particulièrement utile lorsque votre modèle objet impose l'utilisation de noms identiques pour des procédures qui s'appliquent à des types de données différents.  Par exemple, les procédures `Display` d'une classe pouvant afficher plusieurs types de données distincts peuvent se présenter comme suit :  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#64)]  
  
 Sans surcharge, vous devez créer des noms distincts pour chacune des procédures, même si celles\-ci effectuent les mêmes tâches, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#65)]  
  
 La surcharge facilite l'utilisation des propriétés ou des méthodes, car elle propose un choix de divers types de données disponibles.  Par exemple, la méthode `Display` surchargée décrite ci\-dessus peut être appelée par l'une des lignes de code suivantes :  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#66)]  
  
 Au moment de l'exécution, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] appelle la procédure correcte en fonction des types de données des paramètres spécifiés.  
  
## Règles de surcharge  
 Pour créer un membre surchargé d'une classe, ajoutez au moins deux propriétés ou méthodes portant le même nom.  Hormis les membres dérivés surchargés, chaque membre surchargé doit posséder des listes distinctes de paramètres, et les éléments suivants ne peuvent pas être utilisés pour opérer une distinction lors de la surcharge d'une propriété ou d'une procédure :  
  
-   modificateurs \(par exemple `ByVal` ou `ByRef`\) qui s'appliquent à un membre ou à des paramètres du membre ;  
  
-   noms de paramètres ;  
  
-   types de retour de procédures.  
  
 Le mot clé `Overloads` est facultatif lors de la surcharge, mais si un membre surchargé l'utilise, tous les autres membres surchargés portant le même nom doivent également spécifier ce mot clé.  
  
 Les classes dérivées peuvent surcharger les membres hérités avec des membres dont les paramètres et les types de paramètre sont identiques ; ce processus porte le nom d'*occultation par le nom et la signature*.  Si le mot clé `Overloads` est utilisé lors de l'occultation par le nom et la signature, l'implémentation de la classe dérivée du membre sera utilisée à la place de l'implémentation dans la classe de base, et toutes les autres surcharges de ce membre seront disponibles pour les instances de la classe dérivée.  
  
 Si le mot clé `Overloads` est omis lors de la surcharge d'un membre hérité avec un membre dont les paramètres et les types de paramètre sont identiques, la surcharge est appelée l'*occultation par le nom*.  L'occultation par le nom remplace l'implémentation héritée d'un membre et rend toutes les autres surcharges indisponibles pour les instances de la classe dérivée et ses descendants.  
  
 Les modificateurs `Overloads` et `Shadows` ne peuvent pas être utilisés avec la même propriété ou méthode.  
  
### Exemple  
 L'exemple suivant crée des méthodes surchargées qui acceptent une valeur de type `String` ou `Decimal` correspondant à un montant en dollars et qui retournent une chaîne comportant le taux de T.V.A.  
  
##### Pour utiliser cet exemple afin de créer une méthode surchargée  
  
1.  Ouvrez un nouveau projet et ajoutez une classe appelée `TaxClass`  
  
2.  Ajoutez le code suivant à la classe `TaxClass` :  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#67)]  
  
3.  Ajoutez la procédure suivante à votre formulaire :  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#68)]  
  
4.  Ajoutez un bouton à votre formulaire et appelez la procédure `ShowTax` à partir de l'événement de bouton `Button1_Click`.  
  
5.  Exécutez le projet et cliquez sur le bouton du formulaire afin de tester la procédure surchargée `ShowTax`.  
  
 Au moment de l'exécution, le compilateur sélectionne la fonction surchargée adéquate qui correspond aux paramètres utilisés.  Lorsque vous cliquez sur le bouton, la méthode surchargée est d'abord appelée avec un paramètre `Price` \(une chaîne\) ; le message "Price is a String.  Tax is $5,12" s'affiche.  La deuxième fois, `TaxAmount` est appelé avec une valeur`Decimal` et le message "Price is a Decimal.  Tax is $5,12" s'affiche.  
  
## Voir aussi  
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)