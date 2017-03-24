---
title: "How to: Check Connection Status in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Web connections"
  - "IsAvailable property, about IsAvailable"
  - "connections, checking status"
  - "connection status"
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# How to: Check Connection Status in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La propriété <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> peut être utilisée pour déterminer si l'ordinateur dispose d'un réseau actif ou d'une connexion Internet.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour vérifier si un ordinateur a une connexion active  
  
-   Déterminez si la propriété `IsAvailable` a la valeur `True` ou `False`.  Le code suivant vérifie l'état de la propriété et le signale :  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Connectivité et réseau**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>