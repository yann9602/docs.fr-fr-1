---
title: "Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 34b222bdbfdae0673b7150c220ca477b7e286dda
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Comment : déclarer des événements personnalisés pour éviter les blocages (Visual Basic)
Il existe plusieurs cas où il est important de ce gestionnaire d’un événements ne bloque pas les gestionnaires d’événements suivants. Événements personnalisés permettent à l’événement à appeler ses gestionnaires d’événements de façon asynchrone.  
  
 Par défaut, le champ du magasin de stockage pour une déclaration d’événement est un délégué multicast qui associe en série tous les gestionnaires d’événements. Cela signifie que si un gestionnaire met un certain temps, il bloque les autres gestionnaires jusqu'à la fin. (Gestionnaires d’événements valides doivent jamais exécuter des opérations longues ou potentielles de blocage).  
  
 Au lieu d’utiliser l’implémentation par défaut d’événements Visual Basic, vous pouvez utiliser un événement personnalisé pour exécuter les gestionnaires d’événements de façon asynchrone.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, le `AddHandler` accesseur ajoute le délégué pour chaque gestionnaire de la `Click` événement un <xref:System.Collections.ArrayList>stockés dans le `EventHandlerList` champ.</xref:System.Collections.ArrayList>  
  
 Lorsque le code déclenche le `Click` événement, le `RaiseEvent` accesseur appelle tous les délégués de gestionnaires d’événements de façon asynchrone à l’aide de la <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>méthode.</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> Cette méthode appelle chaque gestionnaire sur un thread de travail et retourne immédiatement, donc les gestionnaires ne peut pas se bloquer mutuellement.  
  
 [!code-vb[27 VbVbalrEvents](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.ArrayList></xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Guide pratique : déclarer des événements personnalisés pour économiser la mémoire](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
