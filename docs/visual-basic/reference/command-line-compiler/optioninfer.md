---
title: "/optioninfer | Microsoft Docs"
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
  - "/optioninfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-optioninfer compiler option [Visual Basic]"
  - "/optioninfer compiler option [Visual Basic]"
  - "optioninfer compiler option [Visual Basic]"
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optioninfer
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permet l'utilisation de l'inférence de type de variable locale dans les déclarations de variable.  
  
## Syntaxe  
  
```  
/optioninfer[+ | -]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`+`  &#124; `-`|Facultatif.  Spécifiez `/optioninfer+` pour activer l'inférence de type de variable locale ou `/optioninfer-` pour la bloquer.  L'option `/optioninfer`, sans aucune valeur spécifiée, est identique à `/optioninfer+`.  La valeur par défaut en l'absence du commutateur `/optioninfer` est aussi `/optioninfer+`.  La valeur par défaut est définie dans le fichier réponse Vbc.rsp.|  
  
> [!NOTE]
>  Vous pouvez utiliser l'option `/noconfig` pour conserver les valeurs par défaut internes du compilateur au lieu de celles spécifiées dans le fichier vbc.rsp.  Pour cette option, la valeur par défaut du compilateur est `/optioninfer-`.  
  
## Notes  
 Si le fichier de code source contient une [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), l'instruction substitue le paramètre du compilateur de ligne de commande `/optioninfer`.  
  
### Pour définir \/optioninfer dans l'IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/fr-fr/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Sous l'onglet **Compiler**, modifiez la valeur figurant dans la zone **Option infer**.  
  
## Exemple  
 Le code suivant compile `test.vb` avec l'inférence de type de variable locale activée.  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)