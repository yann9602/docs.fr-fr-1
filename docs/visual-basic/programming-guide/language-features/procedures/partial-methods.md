---
title: "Partial Methods (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.PartialMethod"
  - "PartialMethod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "custom logic into code [Visual Basic]"
  - "partial methods [Visual Basic]"
  - "partial, methods [Visual Basic]"
  - "methods [Visual Basic], partial methods"
  - "inserting custom logic into code"
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Partial Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les méthodes partielles permettent aux développeurs d'insérer une logique personnalisée dans le code.  En général, le code fait partie d'une classe générée par le concepteur.  Les méthodes partielles sont définies dans une classe partielle créée par un générateur de code et sont utilisées couramment pour notifier que quelque chose a été modifié.  Elles permettent au développeur de spécifier un comportement personnalisé en réponse à la modification.  
  
 Le concepteur du générateur de code définit uniquement la signature de méthode et un ou plusieurs appels à la méthode.  Les développeurs peuvent fournir ensuite des implémentations pour la méthode si ils souhaitent personnaliser le comportement du code généré.  Lorsqu'aucune implémentation n'est fournie, les appels à la méthode sont supprimés par le compilateur, sans surcharge supplémentaire des performances.  
  
## Déclaration  
 Le code généré marque la définition d'une méthode partielle en plaçant le mot clé `Partial` au début de la ligne de signature.  
  
```vb#  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 La définition doit remplir les conditions suivantes :  
  
-   La méthode doit être un `Sub`, pas un `Function`.  
  
-   Le corps de la méthode doit rester vide.  
  
-   Le modificateur d'accès doit être `Private`.  
  
## Implémentation  
 L'implémentation consiste principalement à remplir le corps de la méthode partielle.  L'implémentation est en général dans une classe partielle séparée de la définition et est écrite par un développeur qui souhaite étendre le code généré.  
  
```vb#  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 L'exemple précédent duplique exactement la signature dans la déclaration, mais des variations sont possibles.  En particulier, d'autres modificateurs peuvent être ajoutés, tel que `Overloads` ou `Overrides`.  Un seul modificateur `Overrides` est autorisé.  Pour plus d'informations sur les modificateurs de méthode, consultez [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## Utilisation  
 Vous appelez une méthode partielle comme vous appelleriez toute autre procédure `Sub`.  Si la méthode a été implémentée, les arguments sont évalués et le corps de la méthode est exécuté.  Toutefois, souvenez\-vous que l'implémentation d'une méthode partielle est facultative.  Si la méthode n'est pas implémentée, son appel n'a aucun effet et les expressions passées comme arguments à la méthode ne sont pas évaluées.  
  
## Exemple  
 Dans un fichier nommé Product.Designer.vb, définissez une classe `Product` qui a une propriété `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Dans un fichier nommé Product.vb, fournissez une implémentation pour `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Enfin, dans la méthode Main d'un projet, déclarez une instance `Product` et fournissez une valeur initiale pour sa propriété `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Une boîte de message doit afficher la message suivant :  
  
 `Quantity was changed to 100`  
  
## Voir aussi  
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Génération de code dans LINQ to SQL](../Topic/Code%20Generation%20in%20LINQ%20to%20SQL.md)   
 [Ajout d'une logique métier à l'aide de méthodes partielles](../Topic/Adding%20Business%20Logic%20By%20Using%20Partial%20Methods.md)