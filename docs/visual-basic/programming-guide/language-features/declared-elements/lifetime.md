---
title: "Lifetime in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "static variables, lifetime"
  - "static variables, Visual Basic"
  - "declared elements, lifetime"
  - "Shared variable lifetime"
  - "lifetime, declared elements"
  - "lifetime, Visual Basic"
  - "lifetime"
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lifetime in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La *durée de vie* d'un élément déclaré est la période pendant laquelle il est accessible et peut être utilisé.  Les variables sont les seuls éléments qui ont une durée de vie.  Pour cette raison, le compilateur traite les paramètres de procédure et les retours de fonction comme des cas spéciaux de variables.  La durée de vie d'une variable représente la période pendant laquelle elle peut stocker une valeur.  La variable peut voir sa valeur varier au cours de sa durée de vie, mais elle stocke toujours une valeur quelconque.  
  
## Durées de vie différentes  
 Une *variable membre* \(déclarée au niveau du module, à l'extérieur de toute procédure\) a en général le même durée de vie que l'élément dans laquelle elle est déclarée.  Une variable non partagée déclarée dans une classe ou une structure existe en tant que copie séparée pour chaque instance de la classe ou de la structure dans laquelle elle est déclarée.  Chaque variable de ce genre a la même durée de vie que son instance.  Toutefois, une variable `Shared` a une seule durée de vie qui correspond à la durée d'exécution de votre application.  
  
 Une *variable locale* \(déclarée à l'intérieur d'une procédure\) existe uniquement tant que la procédure dans laquelle elle est déclarée s'exécute.  C'est également le cas des paramètres de cette procédure et de tout retour de fonction.  Toutefois, si la procédure appelle d'autres procédures, les variables locales conservent leurs valeurs pendant la durée d'exécution des procédures appelées.  
  
## Début de la durée de vie  
 La durée de vie d'une variable locale commence au moment où le contrôle pénètre dans la procédure dans laquelle elle est déclarée.  Chaque variable locale est initialisée avec la valeur par défaut de son type de données dès que la procédure est exécutée.  Lorsque la procédure rencontre une instruction `Dim` qui spécifie des valeurs initiales, elle donne ces valeurs aux variables, même si votre code leur avait déjà assigné d'autres valeurs.  
  
 Chaque membre d'une variable structure est initialisé comme s'il s'agissait d'une variable distincte.  De la même façon, chaque élément d'une variable tableau est initialisé individuellement.  
  
 Les variables déclarées dans un bloc à l'intérieur d'une procédure \(tel qu'une boucle `For`\) sont initialisées lors de l'entrée dans la procédure.  Ces initialisations entrent en vigueur même si votre code n'exécute pas le bloc.  
  
## Fin de la durée de vie  
 Lorsqu'une procédure se termine, les valeurs de ses variables locales ne sont pas conservées et [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] libère leur mémoire.  La prochaine fois que vous appelez la procédure, toutes ses variables locales sont recréées et réinitialisées.  
  
 Lorsqu'une instance d'une classe ou d'une structure prend fin, ses variables non partagées perdent leur mémoire et leur valeur.  Chaque nouvelle instance de la classe ou de la structure crée et réinitialise ses variables non partagées.  Toutefois, les variables `Shared` sont conservées jusqu'au terme de l'exécution de votre application.  
  
## Extension de la durée de vie  
 Si vous déclarez une variable locale avec le mot clé `Static`, sa durée de vie est plus longue que le temps d'exécution de sa procédure.  Le tableau suivant montre comment la déclaration de procédure détermine la durée de vie d'une variable `Static`.  
  
|Emplacement de procédure et partage|La durée de vie de variable statique commence|La durée de vie de variable statique se termine|  
|-----------------------------------------|---------------------------------------------------|-----------------------------------------------------|  
|Dans un module \(partagé par défaut\)|Au premier appel de la procédure|À l'arrêt de l'exécution de votre application|  
|Dans une classe, `Shared` \(la procédure n'est pas un membre d'instance\)|Au premier appel de la procédure sur une instance spécifique ou sur le nom de classe ou de structure lui\-même|À l'arrêt de l'exécution de votre application|  
|Dans une instance d'une classe, non `Shared` \(la procédure est un membre d'instance\)|Au premier appel de la procédure sur une instance spécifique|Lorsque l'instance est libérée pour le garbage collection \(GC\)|  
  
## Variables statiques du même nom  
 Vous pouvez déclarer des variables statiques avec le même nom dans plusieurs procédures.  Dans ce cas, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considère chacune des variables comme un élément distinct.  L'initialisation d'une de ces variables n'affecte pas les valeurs des autres.  C'est également vrai si vous définissez une procédure avec un ensemble de surcharges et que vous déclarez une variable statique avec le même nom dans chaque surcharge.  
  
## Éléments conteneurs pour les variables statiques  
 Vous pouvez déclarer une variable locale statique dans une classe, c'est\-à\-dire dans une procédure au sein de cette classe.  Toutefois, vous ne pouvez pas déclarer une variable locale statique dans une structure, ni comme membre de structure ni comme variable locale d'une procédure dans cette structure.  
  
## Exemple  
  
### Description  
 L'exemple suivant déclare une variable à l'aide du mot clé [Static](../../../../visual-basic/language-reference/modifiers/static.md).  \(Notez que vous n'avez pas besoin du mot clé `Dim` lorsque [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) utilise un modificateur, tel que `Static`.\)  
  
### Code  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### Commentaires  
 Dans l'exemple précédent, la variable `applesSold` continue d'exister après que la procédure `runningTotal` retourne au code appelant.  La prochaine fois que `runningTotal` est appelé, `applesSold` conserve sa valeur précédemment calculée.  
  
 Si `applesSold` avait été déclaré sans utiliser `Static`, les valeurs précédemment accumulées n'auraient pas été conservées d'un appel à l'autre à `runningTotal`.  Au prochain appel de `runningTotal`, `applesSold` aurait été recréé et initialisé à 0 et `runningTotal` aurait simplement retourné la même valeur que celle avec laquelle elle avait été appelée.  
  
### Compilation du code  
 Vous pouvez initialiser la valeur d'une variable locale statique dans sa déclaration.  Si vous déclarez un tableau `Static`, vous pouvez initialiser son rang \(nombre de dimensions\), la longueur de chaque dimension et les valeurs de chaque élément.  
  
### Sécurité  
 Dans l'exemple précédent, vous pouvez obtenir la même durée de vie en déclarant `applesSold` au niveau du module.  Toutefois, si vous avez modifié de la sorte la portée d'une variable, la procédure ne dispose plus d'un accès exclusif à celle\-ci.  Dans la mesure où d'autres procédures peuvent accéder à `applesSold` et modifier sa valeur, le total évolutif n'est plus fiable et le code est plus difficile à gérer.  
  
## Voir aussi  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)