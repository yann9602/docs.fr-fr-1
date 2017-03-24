---
title: "How to: Receive Strings From Serial Ports in Visual Basic | Microsoft Docs"
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
  - "serial ports, retrieving strings"
  - "strings [Visual Basic], retrieving from serial ports"
  - "My.Resources object"
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Receive Strings From Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique explique comment utiliser `My.Computer.Ports` pour recevoir des chaînes des ports série de l'ordinateur en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
### Pour recevoir des chaînes du port série  
  
1.  Initialisez la chaîne de retour.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Déterminez quel port série doit fournir les chaînes.  Cet exemple suppose que c'est le port `COM1`.  
  
3.  Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Le bloc `Try...Catch...Finally` permet à l'application de fermer le port série même s'il génère une exception.  Tout le code qui manipule le port série doit apparaître dans ce bloc.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Créez une boucle `Do` pour lire les lignes de texte jusqu'à ce qu'il ne reste plus aucune ligne disponible.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Utilisez la méthode <xref:System.IO.Ports.SerialPort.ReadLine%2A> pour lire la ligne de texte disponible suivante à partir du port série.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Utilisez une instruction `If` pour déterminer si la méthode <xref:System.IO.Ports.SerialPort.ReadLine%2A> retourne `Nothing` \(ce qui signifie qu'il n'y a plus de texte disponible\).  Si elle retourne `Nothing`, quittez la boucle `Do`.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Ajoutez un bloc `Else` à l'instruction `If` pour gérer le cas si la chaîne est effectivement lue.  Le bloc ajoute la chaîne du port série à la chaîne de retour.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Retournez la chaîne.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## Exemple  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Connectivité et réseau**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Compilation du code  
 Cet exemple suppose que l'ordinateur utilise `COM1`.  
  
## Programmation fiable  
 Cet exemple suppose que l'ordinateur utilise `COM1`.  Pour plus de souplesse, le code doit permettre à l'utilisateur de sélectionner le port série dans une liste de ports disponibles.  Pour plus d'informations, consultez [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Cet exemple utilise un bloc `Try...Catch...Finally` pour vérifier que l'application ferme le port et pour intercepter les exceptions d'expiration.  Pour plus d'informations, consultez [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)