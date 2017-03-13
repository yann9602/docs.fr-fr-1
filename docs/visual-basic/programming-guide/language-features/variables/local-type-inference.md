---
title: "Local Type Inference (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "local type inference"
  - "vb.TypeInfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Option Infer statement"
  - "local type inference [Visual Basic]"
  - "implicitly-typed local variables [Visual Basic]"
  - "variables [Visual Basic], type inference"
  - "inference [Visual Basic]"
  - "type inference [Visual Basic]"
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 43
---
# Local Type Inference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Le compilateur Visual Basic utilise l'*inférence de type* pour déterminer les types de données des variables locales déclarées sans clause `As`.  Le compilateur déduit le type de variable à partir du type d'expression d'initialisation.  Cela vous permet de déclarer des variables sans déclarer de type explicitement, comme le montre l'exemple qui suit. Il résulte de ces déclarations que `num1` et `num2` sont fortement typés comme entiers.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
  
> [!NOTE]
>  Si vous ne souhaitez pas que `num2` reçoive le type `Integer` dans l'exemple précédent, vous pouvez spécifier un type différent en utilisant une déclaration telle que `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.  
  
 L'inférence de type locale s'applique au niveau de la procédure.  Elle ne peut pas être utilisée pour déclarer des variables au niveau du module \(dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc\).  Dans l'exemple précédent, si `num2` est un champ d'une classe et non une variable locale d'une procédure, la déclaration génère une erreur si le contrôle `Option Strict` est activé et classe `num2` en tant qu'`Object` si `Option Strict` est désactivé.  De la même façon, l'inférence de type locale ne s'applique pas aux variables au niveau de la procédure déclarées comme `Static`.  
  
## Différences entre l'inférence de type etla liaison tardive  
 Le code qui utilise l'inférence de type ressemble au code basé sur la liaison tardive.  Toutefois, l'inférence de type assigne un type fort à la variable, au lieu de la conserver en tant qu'`Object`.  Le compilateur utilise l'initialiseur de variable, pour déterminer le type de la variable au moment de la compilation et produire le code à liaison anticipée.  Dans l'exemple précédent, `num2`, comme `num1`, est de type `Integer`.  
  
 Le comportement de variables à liaison anticipée diffère de celui des variables à liaison tardive, pour lesquelles le type n'est connu qu'au moment de l'exécution.  Le fait de connaître le type tôt permet au compilateur d'identifier les problèmes avant exécution, d'allouer la mémoire précisément et d'optimiser d'autres aspects.  La liaison anticipée permet également à l'environnement de développement intégré Visual Basic \(IDE\) de fournir l'aide IntelliSense sur les membres d'un objet.  La liaison anticipée est également préférable en termes de performance.  Cela s'explique par le fait que toutes les données stockées dans une variable à liaison tardive doivent être encapsulées en tant que types `Object`, et l'accès aux membres du type au moment de l'exécution ralentit le programme.  
  
## Exemples  
 L'inférence de type se produit lorsqu'une variable locale est déclarée sans clause `As` et qu'elle est initialisée.  Le compilateur utilise le type de la valeur initiale assignée en tant que type de la variable.  Par exemple, chacune des lignes de code suivantes déclare une variable de type `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 Le code suivant démontre deux façons équivalentes de créer une table d'entiers.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 Il est utile d'employer l'inférence de type pour déterminer le type d'une variable de contrôle de boucle.  Dans le code suivant, le compilateur déduit que `number` est de type `Integer` car `someNumbers2` est un tableau d'entiers dans l'exemple précédent.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 L'inférence de type local peut être utilisée dans les instructions `Using` pour établir le type du nom de ressource, comme le montre l'exemple suivant.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 Le type d'une variable peut être également déduit des valeurs de retour de fonctions, comme le montre l'exemple suivant.  `pList1` et `pList2` sont des tableaux de processus car `Process.GetProcesses` retourne un tableau de processus.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## Option Infer  
 `Option Infer` vous permet de spécifier si l'inférence de type local dans un fichier particulier.  Pour activer ou bloquer l'option, tapez l'une des instructions suivantes au début du fichier.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Si vous ne spécifiez aucune valeur pour `Option Infer` dans votre code, la valeur par défaut du compilateur est `Option Infer On`.  Pour les projets mis à niveau à partir de [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb-orcas-long-md.md)] ou d'une version antérieure, la valeur par défaut du compilateur est `Option Infer Off`.  
  
 Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur dans le fichier est prioritaire.  
  
 Pour plus d'informations, consultez [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic).  
  
## Restrictions  
 L'inférence de type ne peut être utilisée que pour les variables locales non statiques ; elle ne peut être utilisée pour déterminer le type des champs de classe, des propriétés ou des fonctions.  
  
## Voir aussi  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [For Each...Next, instruction](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next, instruction](../../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [\/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)