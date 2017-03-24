---
title: "/highentropyva (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/highentropyva"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/highentropyva compiler option [C#]"
  - "-highentropyva compiler option [C#]"
  - "highentropyva compiler option [C#]"
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# /highentropyva (C# Compiler Options)
L'option du compilateur **\/highentropyva** indique le noyau windows si un exécutable particulier prend en charge la randomisation maximale \(ASLR\) de l'espace d'adressage d'entropie.  
  
## Syntaxe  
  
```  
/highentropyva[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Cette option indique qu'un fichier exécutable 64 bits ou un exécutable étant signalée par l'option du compilateur [\/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) prend en charge un espace d'adressage virtuel élevé d'entropie.  L'option est désactivée par défaut.  Utilisez **\/highentropyva\+** ou **\/highentropyva** pour l'activer.  
  
## Notes  
 L'option **\/highentropyva** permet aux versions compatibles du noyau windows d'utiliser des degrés plus élevés d'entropie en rendant aléatoire la disposition de l'espace d'adressage d'un processus dans le cadre de ASLR.  Utiliser des degré plus élevés d'entropie signifie qu'un plus grand nombre d'adresses peuvent être alloués aux zones de mémoire telles que les piles et les segments.  Par conséquent, il est difficile de deviner l'emplacement d'une région particulière de mémoire.  
  
 Lorsque l'option du compilateur **\/highentropyva** est spécifiée, l'exécutable cible tous les modules duquel il dépend doivent être en mesure de gérer les valeurs des pointeurs qui sont supérieures à 4 gigaoctets \(GB\) lorsqu'il s'exécute en tant que processus 64 bits.  
  
 Pour plus d'informations surASLR, consultez [Résoudre les vulnérabilités des logiciels](http://go.microsoft.com/fwlink/?LinkId=226234).