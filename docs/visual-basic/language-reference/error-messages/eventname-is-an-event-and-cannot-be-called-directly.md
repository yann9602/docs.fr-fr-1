---
title: "&#39; &lt;eventname&gt;&#39; est un événement et ne peut pas être appelée directement"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords: BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a>&#39; &lt;eventname&gt;&#39; est un événement et ne peut pas être appelée directement
' <`eventname`>' est un événement et ne peut donc pas être appelé directement. Utilisez un `RaiseEvent` instruction pour déclencher un événement.  
  
 Un appel de procédure spécifie un événement pour le nom de la procédure. Un gestionnaire d’événements est une procédure, mais l’événement lui-même est un dispositif de signalisation qui doit être déclenché et géré.  
  
 **ID d’erreur :** BC32022  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Utilisez un `RaiseEvent` instruction pour signaler un événement et appeler les procédures qui le gèrent.  
  
## <a name="see-also"></a>Voir aussi  
 [RaiseEvent (instruction)](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
