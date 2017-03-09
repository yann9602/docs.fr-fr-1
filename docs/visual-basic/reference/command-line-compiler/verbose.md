---
title: "/verbose | Microsoft Docs"
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
  - "verbose compiler option [Visual Basic]"
  - "-verbose compiler option [Visual Basic]"
  - "/verbose compiler option [Visual Basic]"
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# /verbose
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Entraîne le compilateur à produire un état détaillé et des messages d'erreur.  
  
## Syntaxe  
  
```  
/verbose[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Facultatif.  Spécifier `/verbose` équivaut à spécifier `/verbose+`, ce qui entraîne le compilateur à émettre des messages documentés.  La valeur par défaut pour cette option est `/verbose-`.  
  
## Notes  
 L'option  `/verbose` affiche des informations sur le nombre total d'erreurs émises par le compilateur, signale les assemblys chargés par un module et affiche les fichiers en cours de compilation.  
  
> [!NOTE]
>  L'option `/verbose` n'est pas accessible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `In.vb` et demande au compilateur d'afficher des informations d'état détaillées :  
  
```  
vbc /verbose in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)