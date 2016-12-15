---
title: "Out of stack space (Visual Basic) | Microsoft Docs"
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
  - "vbrID28"
dev_langs: 
  - "VB"
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Out of stack space (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La pile est une zone de mémoire dont la taille augmente ou diminue de manière dynamique en fonction des besoins du programme en cours d'exécution.  Ses limites ont été dépassées.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que les procédures ne sont pas imbriquées trop profondément.  
  
2.  Assurez\-vous que les procédures récursives se terminent correctement.  
  
3.  Si les variables locales requièrent davantage d'espace que la quantité disponible, essayez de déclarer certaines variables au niveau du module.  Vous pouvez également déclarer toutes les variables de la procédure comme statiques en faisant précéder le mot clé `Property`, `Sub` ou `Function` de `Static`.  Vous pouvez aussi utiliser l'instruction `Static` pour déclarer des variables statiques individuelles à l'intérieur de procédures.  
  
4.  Étant donné que les chaînes de longueur fixe utilisent davantage d'espace de pile que les chaînes de longueur variable, redéfinissez certaines chaînes de longueur fixe en chaînes de longueur variable.  Vous pouvez également définir la chaîne au niveau du module où elle ne requiert aucun espace de pile.  
  
5.  Vérifiez le nombre d'appels de fonctions `DoEvents` imbriquées à l'aide de la boîte de dialogue `Calls` pour afficher les procédures actives sur la pile.  
  
6.  Vérifiez que vous n'avez provoqué aucune cascade d'événements en déclenchant un événement qui appelle une procédure événementielle qui se trouve déjà sur la pile.  Une cascade d'événement est semblable à un appel de procédure récursive non terminé, en moins évident, puisque l'appel est effecuté par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] plutôt qu'un appel explicite dans le code.  Utilisez la boîte de dialogue `Calls`pour afficher les procédures actives sur la pile.  
  
## Voir aussi  
 [Fenêtres Mémoire](/visual-studio/debugger/memory-windows)