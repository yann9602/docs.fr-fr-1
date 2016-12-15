---
title: "Option Infer Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.OptionInfer"
  - "vb.Infer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], declaring"
  - "Option Infer statement"
  - "Infer keyword"
  - "declaring variables, inferred"
  - "inferred variable declaration"
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
caps.handback.revision: 72
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Infer Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.  
  
## Syntaxe  
  
```  
Option Infer { On | Off }  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`On`|Facultatif.  Active l'inférence de type de variable locale.|  
|`Off`|Facultatif.  Désactive l'inférence de type de variable locale.|  
  
## Notes  
 Pour définir `Option Infer` dans un fichier, tapez `Option Infer On` ou `Option Infer Off` en haut du fichier, avant tout autre code source.  Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.  
  
 Quand vous affectez à `Option Infer` la valeur `On`, vous pouvez déclarer des variables locales sans déclarer explicitement un type de données.  Le compilateur déduit le type de données d'une variable à partir du type de son expression d'initialisation.  
  
 Dans l'illustration suivante, `Option Infer` est activé.  La variable contenue dans la déclaration `Dim someVar = 2` est déclarée en tant qu'entier par l'inférence de type.  
  
 ![Vue IntelliSense de la déclaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
IntelliSense quand Option Infer est activé  
  
 Dans l'illustration suivante, `Option Infer` est désactivé.  La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type.  Dans cet exemple, le paramètre **Option Strict** a la valeur **Off** dans la [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic).  
  
 ![Vue IntelliSense de la déclaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
IntelliSense quand Option Infer est désactivé  
  
> [!NOTE]
>  Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] effectue des opérations appelées *boxing* et *unboxing* pour procéder à des conversions entre un `Object` et un type de valeur, ce qui ralentit l'exécution.  Pour plus d'informations sur les opérations boxing et unboxing, consultez [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).  
  
 L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.  
  
 Pour plus d'informations, consultez [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## En l'absence d'instruction Option Infer  
 Si le code source ne contient pas d'instruction `Option Infer`, la définition du paramètre **Option Infer** de la [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) est utilisée.  Si le compilateur de ligne de commande est utilisé, l'option de compilateur [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) est utilisée.  
  
#### Pour définir Option Infer dans l'IDE  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/fr-fr/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Définissez la valeur dans la zone **Option infer**.  
  
 Quand vous créez un projet, le paramètre **Option Infer** de l'onglet **Compiler** reprend la définition du paramètre **Option Infer** de la boîte de dialogue **Valeurs par défaut VB**.  Pour accéder à la boîte de dialogue **Valeurs par défaut VB**, dans le menu **Outils**, cliquez sur **Options**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  La définition par défaut initiale de **Valeurs par défaut VB** est `On`.  
  
#### Pour définir Option Infer sur la ligne de commande  
  
-   Incluez l'option de compilateur [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) dans la commande **vbc**.  
  
## Types de données et valeurs par défaut  
 Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.  
  
|||||  
|-|-|-|-|  
|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|  
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé \(par défaut\), la valeur affectée à la variable est `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activée \(par défaut\), la variable prend le type de données de l'initialiseur.  Consultez [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données.  Pour plus d'informations, consultez [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l'initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|  
  
## Exemple  
 Les exemples suivants montrent comment l'instruction `Option Infer` active l'inférence de type de variable locale.  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant montre que le type au moment de l'exécution peut être différent quand une variable est identifiée comme `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## Voir aussi  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)