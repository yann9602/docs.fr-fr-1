---
title: "How to: Dial Modems Attached to Serial Ports in Visual Basic | Microsoft Docs"
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
  - "modems, dialing"
  - "serial ports, dialing"
  - "My.Computer.Ports object"
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Dial Modems Attached to Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette rubrique montre comment utiliser `My.Computer.Ports` pour appeler un modem avec [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 En général, le modem est connecté à l'un des ports série de l'ordinateur.  Pour que votre application communique avec le modem, elle doit envoyer des commandes au port série approprié.  
  
### Pour utiliser un modem  
  
1.  Déterminez le port série auquel le modem est connecté.  Cet exemple suppose que le modem est connecté à COM1.  
  
2.  Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Le bloc `Using` permet à l'application de fermer le port série même s'il génère une exception.  Tout le code qui manipule le port série doit apparaître dans ce bloc ou dans un bloc `Try...Catch...Finally`.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Définissez la propriété `DtrEnable` pour indiquer que l'ordinateur est prêt à accepter une transmission entrante du modem.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Envoyez la commande de numérotation et le numéro de téléphone au modem via le port série à l'aide de la méthode <xref:System.IO.Ports.SerialPort.Write%2A>.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## Exemple  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Connectivité et réseau**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Compilation du code  
 Cet exemple requiert une référence à l'espace de noms <xref:System?displayProperty=fullName>.  
  
## Programmation fiable  
 Cet exemple suppose que le modem est connecté à COM1.  Nous recommandons que votre code permette à l'utilisateur de sélectionner le port série souhaité dans une liste de ports disponibles.  Pour plus d'informations, consultez [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Cet exemple utilise un bloc `Using` pour vérifier que l'application ferme le port même si une exception est levée.  Pour plus d'informations, consultez [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 Dans cet exemple, l'application déconnecte le port série après avoir utilisé le modem.  Dans la pratique, vous souhaitez éventuellement transférer des données au modem et vice versa.  Pour plus d'informations, consultez [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)