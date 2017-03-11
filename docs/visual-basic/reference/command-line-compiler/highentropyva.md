---
title: "/highentropyva (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
helpviewer_keywords: 
  - "highentropyva compiler option (Visual Basic)"
  - "/highentropyva compiler option (Visual Basic)"
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# /highentropyva (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Indique si un fichier exécutable 64 bits ou un fichier exécutable qui est marqué par l'option du compilateur de [\/platform : anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) prend en charge la randomisation élevée de disposition de l'espace d'adressage d' \(ASLR\)entropie.  
  
## Syntaxe  
  
```  
/highentropyva[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Facultatif.  L'option est désactivée par défaut ou si vous spécifiez `/highentropyva-`.  L'option est activée si vous spécifiez `/highentropyva` ou `/highentropyva+`.  
  
## Notes  
 Si vous spécifiez cette option, les versions compatibles du noyau windows peuvent utiliser des niveaux plus élevés d'entropie lorsque le noyau randomise la disposition de l'espace d'adressage d'un processus dans le cadre de ASLR.  Si le noyau utilise des niveaux plus élevés d'entropie, un plus grand nombre d'adresses peut être allouée aux régions de mémoire telles que des piles et les tas.  Par conséquent, il est plus difficile à deviner l'emplacement d'une zone de mémoire particulière.  
  
 Quand l'option est activée, l'exécutable cible et tous les modules dont elle dépend doivent pouvoir gérer les valeurs de type pointeur supérieures à 4 gigaoctets \(GB\) lorsque ces modules s'exécutent en tant que processus 64 bits.  
  
 Pour plus d'informations sur ASLR, consultez [Failles logicielles d'atténuation](http://go.microsoft.com/fwlink/?LinkId=226234).  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)