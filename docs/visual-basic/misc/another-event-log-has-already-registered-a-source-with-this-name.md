---
title: "Une source de ce nom a d&#233;j&#224; &#233;t&#233; inscrite dans un autre journal des &#233;v&#233;nements. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une source de ce nom a d&#233;j&#224; &#233;t&#233; inscrite dans un autre journal des &#233;v&#233;nements.
Il a été tenté d’écrire une entrée dans un journal d’événements dans lequel la source spécifiée est inscrite dans un autre journal d’événements.  
  
 Vous devez définir la propriété <xref:System.Diagnostics.EventLog.Source%2A> de l’instance de votre composant <xref:System.Diagnostics.EventLog> avant que celui\-ci écrive une entrée dans un journal. Dans ce cas, le système vérifie que la source que vous avez spécifiée est inscrite dans le journal d’événements dans lequel le composant écrit et appelle <xref:System.Diagnostics.EventLog.CreateEventSource%2A>, si nécessaire.  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’association entre la source et le premier journal à l’aide de la méthode <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>.  
  
2.  Inscrivez la source dans le nouveau journal.  
  
## Voir aussi  
 [My.Application.Log, objet](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/fr-fr/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/fr-fr/948ff920-a739-4e66-a191-ee951512d42c)