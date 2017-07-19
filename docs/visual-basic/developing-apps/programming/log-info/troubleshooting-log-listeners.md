---
title: "Dépannage : écouteurs de journalisation (Visual Basic) │ Microsoft Docs"
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
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: 11
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
ms.openlocfilehash: b651902563a60a68443f7d3f3b917a9c1ae085bc
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Dépannage : écouteurs de journalisation (Visual Basic)
Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.  
  
 Pour déterminer les écouteurs de journalisation qui reçoivent ces messages, consultez [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 L’objet `Log` peut utiliser le filtrage de journal pour limiter la quantité d’informations qu’il journalise. Si les filtres sont mal configurés, les journaux peuvent contenir des informations incorrectes. Pour plus d'informations sur le filtrage, consultez [Procédure pas à pas : filtrage de la sortie de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Toutefois, si un journal est mal configuré, vous pouvez avoir besoin de davantage d’informations sur sa configuration actuelle. Vous pouvez accéder à ces informations grâce à la propriété avancée `TraceSource` du journal.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Pour déterminer les écouteurs de journalisation de l’objet Log dans le code  
  
1.  Importez l’espace de noms <xref:System.Diagnostics> au début du fichier de code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Créez une fonction qui retourne une chaîne composée d’informations pour chacun des écouteurs du journal.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Passez la collection des écouteurs de la trace du journal à la fonction `GetListeners` et affichez la valeur de retour.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
