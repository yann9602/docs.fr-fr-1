---
title: "How to: Show Available Serial Ports in Visual Basic | Microsoft Docs"
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
  - "serial ports, availability"
  - "My.Computer.Ports.SerialPortNames property"
  - "My.Computer.Ports object"
  - "ports, serial port availability"
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Show Available Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique décrit comment utiliser `My.Computer.Ports` pour afficher les ports série de l'ordinateur qui sont disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 Pour permettre à l'utilisateur de sélectionner le port à utiliser, les noms des ports série sont placés dans un contrôle <xref:System.Windows.Forms.ListBox>.  
  
## Exemple  
 Cet exemple fait une boucle sur toutes les chaînes que la propriété `My.Computer.Ports.SerialPortNames` retourne.  Ces chaînes sont les noms des ports série disponibles sur l'ordinateur.  
  
 En général, un utilisateur sélectionne le port série que l'application doit utiliser dans la liste de ports disponibles.  Dans cet exemple, les noms de ports série sont stockés dans un contrôle <xref:System.Windows.Forms.ListBox>.  Pour plus d'informations, consultez [ListBox, contrôle](../Topic/ListBox%20Control%20\(Windows%20Forms\).md).  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#45)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Connectivité et réseau**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Une référence de projet à System.Windows.Forms.dll.  
  
-   l'accès aux membres de l'espace de noms <xref:System.Windows.Forms>.  Ajoutez une instruction `Imports` si vous n'utilisez pas des noms de membres qualifiés complets dans votre code.  Pour plus d'informations, consultez [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Que votre formulaire ait un contrôle <xref:System.Windows.Forms.ListBox> nommé `ListBox1`.  
  
## Programmation fiable  
 Vous ne devez pas utiliser le contrôle <xref:System.Windows.Forms.ListBox> pour afficher les noms de ports série disponibles.  À la place, vous pouvez utiliser un <xref:System.Windows.Forms.ComboBox> ou un autre contrôle.  Si l'application n'a pas besoin d'une réponse de l'utilisateur, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.TextBox> pour afficher les informations.  
  
> [!NOTE]
>  Les noms de port retournés par `My.Computer.Ports.SerialPortNames` peuvent être incorrects dans le cas d'une exécution sur Windows 98.  Pour empêcher les erreurs d'application, utilisez la gestion des exceptions, telle que l'instruction `Try...Catch...Finally` ou `Using`, lorsque vous employez les noms de port pour ouvrir des ports.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)