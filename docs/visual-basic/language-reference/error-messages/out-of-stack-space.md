---
title: "(Visual Basic) d’espace de pile | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
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
ms.openlocfilehash: 6343767da28ea4e02f9443006b222640755f7882
ms.lasthandoff: 03/13/2017

---
# <a name="out-of-stack-space-visual-basic"></a>Espace de pile insuffisant (Visual Basic)
La pile est une zone de mémoire qui augmente ou diminue dynamiquement aux besoins de votre programme en cours d’exécution. Ses limites ont été dépassées.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez que les procédures ne sont pas imbriqués trop profondément.  
  
2.  Assurez-vous que les procédures récursives se terminent correctement.  
  
3.  Si les variables locales requièrent davantage local variable d’espace disponible, essayez de déclarer des variables au niveau du module. Vous pouvez également déclarer toutes les variables dans la procédure statique en faisant précéder le `Property`, `Sub`, ou `Function` mot clé with `Static`. Vous pouvez également utiliser la `Static` instruction pour déclarer des variables statiques individuelles au sein de procédures.  
  
4.  Redéfinir certains de vos chaînes de longueur fixe en tant que chaînes de longueur variable, comme les chaînes de longueur fixe utilisent davantage d’espace pile que les chaînes de longueur variable. Vous pouvez également définir la chaîne au niveau du module où elle ne requiert aucun espace de pile.  
  
5.  Vérifiez le nombre d’imbriquée `DoEvents` appels de fonctions, à l’aide de la `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.  
  
6.  Assurez-vous que vous n’avez pas provoqué une « cascade d’événements » en déclenchant un événement qui appelle une procédure d’événement déjà sur la pile. Une cascade d’événements est similaire à un appel de procédure récursive inachevé, mais il est moins évident, puisque l’appel est effectué par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] plutôt qu’un appel explicit dans le code. Utilisez le `Calls`boîte de dialogue pour afficher les procédures actives sur la pile.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres Mémoire](https://docs.microsoft.com/visualstudio/debugger/memory-windows)
