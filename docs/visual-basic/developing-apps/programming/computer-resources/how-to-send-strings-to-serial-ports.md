---
title: "How to: Send Strings to Serial Ports in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ports, sending strings to"
  - "strings [Visual Basic], sending to serial ports"
  - "My.Computer.Ports object"
  - "serial ports, sending strings to"
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Send Strings to Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser `My.Computer.Ports` pour envoyer des chaînes aux ports série de l'ordinateur en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Exemple  
 Cet exemple envoie une chaîne au port série COM1.  Vous pouvez être amené à utiliser un port série différent sur votre ordinateur.  
  
 Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 Le bloc `Using` permet à l'application de fermer le port série même s'il génère une exception.  Tout le code qui manipule le port série doit apparaître dans ce bloc ou dans un bloc `Try...Catch...Finally`.  
  
 La méthode <xref:System.IO.Ports.SerialPort.WriteLine%2A> envoie les données au port série.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## Compilation du code  
  
-   Cet exemple suppose que l'ordinateur utilise `COM1`.  
  
## Programmation fiable  
 Cet exemple suppose que l'ordinateur utilise `COM1`. Pour une plus grande souplesse, le code doit autoriser l'utilisateur à sélectionner le port souhaité dans une liste de ports disponibles.  Pour plus d'informations, consultez [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Cet exemple utilise un bloc `Using` pour vérifier que l'application ferme le port même si une exception est levée.  Pour plus d'informations, consultez [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)