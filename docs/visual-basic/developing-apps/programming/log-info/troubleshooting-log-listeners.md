---
title: "Troubleshooting: Log Listeners (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "event logs, troubleshooting"
  - "troubleshooting Visual Basic, event logs"
  - "troubleshooting event logs"
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting: Log Listeners (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.  
  
 Pour déterminer quels écouteurs de journalisation reçoivent ces messages, consultez [Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 L'objet `Log` peut utiliser le filtrage de journal pour limiter la quantité d'informations qu'il enregistre.  Si les filtres ne sont pas correctement configurés, les journaux peuvent contenir de fausses informations.  Pour plus d'informations sur le filtrage, consultez [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Toutefois, même si un journal n'est pas correctement configuré, vous pouvez avoir besoin de plus d'informations sur sa configuration actuelle.  Vous pouvez obtenir ces informations par le biais de la propriété `TraceSource` avancée du journal.  
  
### Pour déterminer les écouteurs de journalisation de l'objet Log dans le code  
  
1.  Importez l'espace de noms <xref:System.Diagnostics> au début du fichier de code.  Pour plus d'informations, consultez [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Créez une fonction qui retourne une chaîne qui se compose d'informations relatives à chacun des écouteurs du journal.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Passez la collection des écouteurs de la trace du journal à la fonction `GetListeners` et affichez la valeur de retour.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)