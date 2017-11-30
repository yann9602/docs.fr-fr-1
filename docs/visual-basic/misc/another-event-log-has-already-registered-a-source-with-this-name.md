---
title: "Une source de ce nom a déjà été inscrite dans un autre journal des événements."
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Une source de ce nom a déjà été inscrite dans un autre journal des événements.
Il a été tenté d’écrire une entrée dans un journal d’événements dans lequel la source spécifiée est inscrite dans un autre journal d’événements.  
  
 Vous devez définir la propriété <xref:System.Diagnostics.EventLog.Source%2A> de l’instance de votre composant <xref:System.Diagnostics.EventLog> avant que celui-ci écrive une entrée dans un journal. Dans ce cas, le système vérifie que la source que vous avez spécifiée est inscrite dans le journal d’événements dans lequel le composant écrit et appelle <xref:System.Diagnostics.EventLog.CreateEventSource%2A> , si nécessaire.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Supprimez l’association entre la source et le premier journal à l’aide de la méthode <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> .  
  
2.  Inscrivez la source dans le nouveau journal.  
  
## <a name="see-also"></a>Voir aussi  
 [My.Application.Log (objet)](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [Comment : supprimer une Source d’événement](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [Comment : ajouter votre Application en tant que Source d’entrées de journal des événements](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
