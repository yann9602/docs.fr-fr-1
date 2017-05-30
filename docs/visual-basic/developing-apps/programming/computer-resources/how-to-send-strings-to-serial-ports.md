---
title: "Guide pratique pour envoyer des chaînes aux ports série en Visual Basic | Microsoft Docs"
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
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 14c5de8d0fa8195129b7ae65c1d373834307488a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Guide pratique pour envoyer des chaînes aux ports série en Visual Basic
Cette rubrique explique comment utiliser `My.Computer.Ports` pour envoyer des chaînes aux ports série de l’ordinateur en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="example"></a>Exemple  
 Cet exemple envoie une chaîne au port série COM1. Vous devrez peut-être utiliser un autre port série de votre ordinateur.  
  
 Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception. Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.  
  
 La méthode <xref:System.IO.Ports.SerialPort.WriteLine%2A> envoie les données au port série.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Cet exemple suppose que l’ordinateur utilise `COM1`.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Cet exemple suppose que l’ordinateur utilise `COM1`. Pour plus de souplesse, le code doit autoriser l’utilisateur à sélectionner le port série dans la liste des ports disponibles. Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception. Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [Guide pratique pour passer des appels avec des modems attachés aux ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [Guide pratique : afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
