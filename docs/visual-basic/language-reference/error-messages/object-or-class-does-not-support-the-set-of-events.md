---
title: "L'objet ou la classe ne prend pas en charge le jeu d'événements"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>L'objet ou la classe ne prend pas en charge le jeu d'événements
Vous avez essayé d’utiliser un `WithEvents` variable avec un composant qui ne peut pas fonctionner en tant que source d’événements pour le jeu d’événements spécifié. Par exemple, vous souhaitez recevoir les événements d’un objet, puis créer un autre objet qui `Implements` le premier objet. Même si vous pensez que vous pouvez recevoir les événements de l’objet implémenté, ce n’est pas toujours le cas. `Implements`implémente uniquement une interface pour les méthodes et propriétés. `WithEvents`n’est pas prise en charge privé `UserControls`, car les informations de type nécessaires pour déclencher le `ObjectEvent` n’est pas disponible au moment de l’exécution.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vous ne pouvez pas recevoir d’événements pour un composant qui ne fournit pas d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Implements (instruction)](../../../visual-basic/language-reference/statements/implements-statement.md)
