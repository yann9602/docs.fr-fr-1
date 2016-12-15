---
title: "/optionstrict | Microsoft Docs"
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
  - "/optionstrict"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-optionstrict compiler option [Visual Basic]"
  - "optionstrict compiler option [Visual Basic]"
  - "/optionstrict compiler option [Visual Basic]"
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optionstrict
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Applique une sémantique de type stricte pour limiter les conversions de types implicites.  
  
## Syntaxe  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Facultatif.  L'option `/optionstrict+` restreint les conversions de types implicites.  La valeur par défaut pour cette option est `/optionstrict-`.  L'option `/optionstrict+` est identique à `/optionstrict`.  Vous pouvez utiliser les deux pour la sémantique de type permissive.  
  
 `custom`  
 Obligatoire.  Avertir lorsque la syntaxe de langue stricte n'est pas respectée.  
  
## Notes  
 Lorsque `/optionstrict+` est appliqué, seules les conversions étendues peuvent être effectuées implicitement.  Les conversions restrictives implicites, telles que l'assignation d'un objet de type `Decimal` à un objet de type entier, sont signalées comme des erreurs.  
  
 Pour générer des avertissements pour les conversions restrictives implicites, utilisez `/optionstrict:custom`.  Utilisez `/nowarn:numberlist` pour ignorer certains avertissements et `/warnaserror:numberlist` pour traiter d'autres comme des erreurs.  
  
### Pour définir \/optionstrict dans l'IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**. Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Modifiez la valeur dans la zone **Option Strict**.  
  
### Pour définir \/optionstrict par programme  
  
-   Consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## Exemple  
 Le code suivant compile `Test.vb` en utilisant une sémantique de type stricte.  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)   
 [\/warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)