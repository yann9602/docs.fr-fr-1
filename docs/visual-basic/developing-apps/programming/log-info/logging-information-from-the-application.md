---
title: "Enregistrement d&quot;informations provenant de l&quot;application (Visual Basic) │ Microsoft Docs"
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
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
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
ms.openlocfilehash: 25bf4e1d8b9b87c1545272c0d2746dc808d3fa4b
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="logging-information-from-the-application-visual-basic"></a>Enregistrement d'informations provenant de l'application (Visual Basic)
Cette section contient des rubriques sur l’enregistrement d’informations provenant de l’application à l’aide de l’objet `My.Application.Log` ou `My.Log`, et sur l’extension des fonctionnalités de journalisation de l’application.  
  
 L’objet `Log` fournit des méthodes pour écrire des informations dans les écouteurs de journalisation de l’application, et la propriété `TraceSource` avancée de l’objet `Log` fournit des informations de configuration détaillées. L’objet `Log` est configuré par le fichier de configuration de l’application.  
  
 L’objet `My.Log` est disponible uniquement pour les applications ASP.NET. Pour les applications clientes, utilisez `My.Application.Log`. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Tâches  
  
|Pour|Voir|  
|--------|---------|  
|Écrire des informations sur les événements dans les journaux de l’application.|[Guide pratique : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Écrire des informations sur les exceptions dans les journaux de l’application.|[Guide pratique : enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Écrire des informations de traçage dans les journaux de l’application quand l’application démarre et s’arrête.|[Guide pratique : enregistrer des messages quand l’application démarre ou s’arrête](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Configurer `My.Application.Log` pour écrire des informations dans un fichier texte.|[Guide pratique : écrire des informations sur des événements dans un fichier texte](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Configurer `My.Application.Log` pour écrire des informations dans un journal des événements.|[Guide pratique : écrire dans le journal des événements de l’application](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Changer l’emplacement où `My.Application.Log` écrit les informations.|[Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Déterminer l’emplacement où `My.Application.Log` écrit les informations.|[Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|Créer un écouteur de journalisation personnalisé pour `My.Application.Log`.|[Procédure pas à pas : création d’écouteurs de journalisation personnalisés](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|Filtrer la sortie des journaux `My.Application.Log`.|[Procédure pas à pas : filtrage de la sortie de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Dépannage : écouteurs de journalisation](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
