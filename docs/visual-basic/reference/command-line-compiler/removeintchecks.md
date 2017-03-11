---
title: "/removeintchecks | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "removeintchecks"
  - "/removeintchecks"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "removeintchecks compiler option [Visual Basic]"
  - "/removeintchecks compiler option [Visual Basic]"
  - "-removeintchecks compiler option [Visual Basic]"
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# /removeintchecks
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Active ou désactive la vérification d'erreurs de dépassement durant les opérations sur les entiers.  
  
## Syntaxe  
  
```  
/removeintchecks[+ | -]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`+`  &#124; `-`|Facultatif.  L'option d' `/removeintchecks-` fait pour activer le compilateur tous les calculs entiers pour les erreurs de dépassement de capacité.  La valeur par défaut est `/removeintchecks-`.<br /><br /> Si vous spécifiez `/removeintchecks` ou `/removeintchecks+`, la vérification d'erreurs ne sera pas activée et les calculs d'entier pourront être plus rapides.  Cependant, sans une vérification des erreurs, des résultats erronés peuvent être stockés sans être signalés si les capacités de type données sont dépassées.|  
  
||  
|-|  
|Pour définir \/removeintchecks dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Cliquez sur le bouton **Avancé**.<br />4.  Modifiez la valeur de la zone **Supprimer les contrôles de dépassement sur les entiers**.|  
  
## Exemple  
 Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement sur les entiers.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)