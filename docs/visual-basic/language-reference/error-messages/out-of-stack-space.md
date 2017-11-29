---
title: Espace de pile insuffisant (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a>Espace de pile insuffisant (Visual Basic)
La pile est une zone de travail de la mémoire augmente et se réduit dynamiquement aux demandes de votre programme en cours d’exécution. Ses limites ont été dépassées.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez que les procédures ne sont pas imbriquées trop profondément.  
  
2.  Assurez-vous que les procédures récursives se terminent correctement.  
  
3.  Si les variables locales requièrent davantage d’espace de variable locale qu’il n’est disponible, essayez de déclarer des variables au niveau du module. Vous pouvez également déclarer toutes les variables dans la procédure statique en faisant précéder le `Property`, `Sub`, ou `Function` mot clé with `Static`. Vous pouvez également utiliser la `Static` instruction pour déclarer des variables statiques individuelles au sein de procédures.  
  
4.  Redéfinissez certaines de vos chaînes de longueur fixe en tant que chaînes de longueur variable, comme les chaînes de longueur fixe utilisent davantage d’espace de pile que les chaînes de longueur variable. Vous pouvez également définir la chaîne au niveau du module où elle ne requiert aucun espace de pile.  
  
5.  Vérifiez le nombre d’imbriquée `DoEvents` appels de fonctions, à l’aide de la `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.  
  
6.  Assurez-vous que vous n’avez pas provoqué une « cascade d’événements » en déclenchant un événement qui appelle une procédure événementielle déjà sur la pile. Une cascade d’événements est similaire à un appel de procédure récursive inachevé, mais il est moins évidente, étant donné que l’appel est effectué par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] au lieu d’un appel explicite dans le code. Utilisez le `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres Mémoire](/visualstudio/debugger/memory-windows)
