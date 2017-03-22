---
title: /highentropyva (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34987930b3afd6d95d12190172a5a5e512106f8a
ms.lasthandoff: 03/13/2017

---
# <a name="highentropyva-visual-basic"></a>/highentropyva (Visual Basic)
Indique si un exécutable 64 bits ou qui est marquée par le [/Platform : anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) option du compilateur prend en charge l’entropie élevée adresse espace Layout Randomization (ASLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. L’option est désactivée par défaut ou si vous spécifiez `/highentropyva-`. L’option est activée si vous spécifiez `/highentropyva` ou `/highentropyva+`.  
  
## <a name="remarks"></a>Remarques  
 Si vous spécifiez cette option, les versions compatibles du noyau Windows peuvent utiliser un degré d’entropie lorsque le noyau rend aléatoire la disposition de l’espace adresse d’un processus dans le cadre de l’ASLR. Si le noyau utilise un degré d’entropie, un plus grand nombre d’adresses peut être alloué à des régions de mémoire telles que les piles et les segments. Par conséquent, il est plus difficile de deviner l’emplacement d’une région de mémoire particulière.  
  
 Lorsque l’option est activée, l’exécutable cible et tous les modules sur dont il dépend doit être en mesure de traiter les valeurs de pointeur sont supérieures à 4 gigaoctets (Go) lorsque ces modules sont exécutent en tant que processus 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
