---
title: "Procedure Overloading (Visual Basic) | Microsoft Docs"
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
  - "signatures"
  - "Overloads keyword"
  - "hiding by signature"
  - "Visual Basic code, procedures"
  - "procedures, signatures for"
  - "procedures, overloading"
  - "procedures, multiple versions"
  - "parameters, lists"
  - "signatures, procedure"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "Shadows keyword"
  - "procedure overloading"
  - "procedures, parameter lists"
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Procedure Overloading (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La *surcharge* d'une procédure consiste à définir celle\-ci en plusieurs versions, à l'aide du même nom, mais avec des listes de paramètres différentes.  La finalité d'une surcharge est de définir plusieurs versions de procédures étroitement liées sans avoir à les différencier par nom.  Pour ce faire, vous devez faire varier la liste des paramètres.  
  
## Règles de surcharge  
 Lorsque vous surchargez une procédure, les règles suivantes s'appliquent :  
  
-   **Même nom**.  Chaque version surchargée doit utiliser le même nom de procédure.  
  
-   **Signature différente**.  Chaque version surchargée doit être différente de toutes les autres versions surchargées sur au moins l'un des points suivants :  
  
    -   Nombre de paramètres  
  
    -   Ordre des paramètres  
  
    -   Types de données des paramètres  
  
    -   Nombre de paramètres de type \(pour une procédure générique\)  
  
    -   Type de retour \(uniquement pour un opérateur de conversion\)  
  
     Avec le nom de procédure, les éléments précédents sont appelés collectivement *signature* de la procédure.  Lorsque vous appelez une procédure surchargée, le compilateur utilise la signature pour vérifier que l'appel correspond bien à la définition.  
  
-   **Éléments ne faisant pas partie de la signature**.  Vous ne pouvez pas surcharger une procédure sans faire varier la signature.  En particulier, vous ne pouvez pas surcharger une procédure en faisant varier uniquement un ou plusieurs des éléments suivants :  
  
    -   Mots clés de modificateur de procédure, tels que `Public`, `Shared` et `Static`  
  
    -   Noms de paramètres ou de paramètres de type  
  
    -   Contraintes de paramètre de type \(pour une procédure générique\)  
  
    -   Mots clés de modificateur de paramètre, tels que `ByRef` et `Optional`  
  
    -   S'il retourne une valeur  
  
    -   Type de données de la valeur de retour \(à l'exception d'un opérateur de conversion\)  
  
     Les éléments de la liste précédente ne font pas partie de la signature.  Bien que vous ne puissiez pas les utiliser pour différencier des versions surchargées, vous pouvez les faire varier parmi des versions surchargées qui sont correctement différenciées par leurs signatures.  
  
-   **Arguments à liaison tardive**.  Si vous essayez de passer une variable objet à liaison tardive à une procédure surchargée, vous devez déclarer le paramètre approprié comme <xref:System.Object>.  
  
## Versions multiples d'une procédure  
 Supposons que vous écriviez une procédure `Sub` pour publier une transaction relative au solde d'un client, et que vous vouliez faire référence au client par son nom ou son numéro de compte.  Pour ce faire, vous pouvez définir deux procédures `Sub` différentes, comme dans l'exemple suivant :  
  
 [!code-vb[VbVbcnProcedures#73](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/procedure-overloading_1.vb)]  
  
### Versions surchargées  
 La première solution consiste à surcharger un seul nom de procédure.  Vous pouvez utiliser le mot clé [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) pour définir une version de la procédure pour chaque liste de paramètres comme suit :  
  
 [!code-vb[VbVbcnProcedures#72](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/procedure-overloading_2.vb)]  
  
#### Surcharges supplémentaires  
 Si vous voulez également accepter le montant d'une transaction sous forme d'un type `Decimal` ou `Single`, vous pouvez surcharger davantage `post` pour permettre cette variation.  Si vous avez effectué cette opération sur chacune des surcharges de l'exemple précédent, vous devez obtenir quatre procédures `Sub` portant toutes le même nom, mais avec quatre signatures différentes.  
  
## Avantages de la surcharge  
 L'avantage présenté par la surcharge d'une procédure réside dans la flexibilité de l'appel.  Pour utiliser la procédure `post` déclarée dans l'exemple précédent, le code appelant peut obtenir l'identification du client selon un type `String` ou `Integer`, puis appeler la même procédure dans les deux cas.  L'exemple suivant illustre ce comportement :  
  
 [!code-vb[VbVbcnProcedures#56](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/procedure-overloading_4.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Types génériques Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)