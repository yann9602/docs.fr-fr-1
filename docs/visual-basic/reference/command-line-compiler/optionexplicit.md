---
title: "/optionexplicit | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optionexplicit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/optionexplicit compiler option [Visual Basic]"
  - "optionexplicit compiler option [Visual Basic]"
  - "-optionexplicit compiler option [Visual Basic]"
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /optionexplicit
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Entraîne le compilateur à signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation.  
  
## Syntaxe  
  
```  
/optionexplicit[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Facultatif.  Spécifiez `/optionexplicit+` pour requérir une déclaration explicite des variables.  L'option `/optionexplicit+` est la valeur par défaut et il s'agit de la même que `/optionexplicit`.  L'option `/optionexplicit-` permet une déclaration implicite des variables.  
  
## Notes  
 Si le fichier de code source contient une [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l'instruction substitue le paramètre du compilateur de ligne de commande `/optionexplicit`.  
  
### Pour définir \/optionexplicit dans l'IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Modifiez la valeur dans la zone **Option Explicit**.  
  
## Exemple  
 Le code suivant compile si `/optionexplicit-` est utilisé.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/optionexplicit_1.vb)]  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)