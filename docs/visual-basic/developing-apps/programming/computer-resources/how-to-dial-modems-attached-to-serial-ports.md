---
title: "Guide pratique pour passer des appels avec des modems attachés aux ports série dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea1b2d6152af8919ac1aa272def4ba198b33867c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Guide pratique pour passer des appels avec des modems attachés aux ports série dans Visual Basic
Cette rubrique explique comment utiliser `My.Computer.Ports` pour passer un appel avec un modem dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 En règle générale, le modem est connecté à l’un des ports série sur l’ordinateur. Pour que l’application puisse communiquer avec le modem, elle doit envoyer des commandes au port série approprié.  
  
### <a name="to-dial-a-modem"></a>Pour communiquer avec un modem  
  
1.  Déterminez le port série auquel le modem est connecté. Cet exemple part du principe que le modem est connecté à COM1.  
  
2.  Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception. Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Définissez la propriété `DtrEnable` pour indiquer que l’ordinateur est prêt à accepter une transmission en provenance du modem.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Envoyez la commande de numérotation et le numéro de téléphone au modem par l’intermédiaire du port série à l’aide de la méthode <xref:System.IO.Ports.SerialPort.Write%2A>.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite une référence à l’espace de noms <xref:System?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Cet exemple part du principe que le modem est connecté à COM1. Nous recommandons que le code autorise l’utilisateur à sélectionner le port série dans la liste des ports disponibles. Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception. Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 Dans cet exemple, l’application déconnecte le port série après avoir utilisé le modem. Dans la pratique, vous souhaiterez transférer des données vers et à partir du modem. Pour plus d’informations, consultez [Guide pratique pour recevoir des chaînes des ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Guide pratique : envoyer des chaînes aux ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Guide pratique : recevoir des chaînes des ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [Guide pratique : afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
