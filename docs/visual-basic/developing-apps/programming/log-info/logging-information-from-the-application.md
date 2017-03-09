---
title: "Logging Information from the Application (Visual Basic) | Microsoft Docs"
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
  - "Log object"
  - "My.Log object"
  - "applications [Visual Basic], logging information from"
  - "logging"
  - "My.Application.Log object"
  - "examples [Visual Basic], logging application information"
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Logging Information from the Application (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette section contient des rubriques qui expliquent comment enregistrer les informations provenant de votre application à l'aide de l'objet `My.Application.Log` ou `My.Log`, et comment étendre les fonctions de journalisation de l'application.  
  
 L'objet `Log` fournit des méthodes permettant d'écrire les informations dans les écouteurs de journalisation de l'application, tandis que la propriété `TraceSource` avancée de l'objet `Log` fournit des informations de configuration détaillées.  L'objet `Log` est configuré par le fichier de configuration de l'application.  
  
 L'objet `My.Log` n'est disponible que pour les applications ASP.NET.  Pour les applications clientes, utilisez `My.Application.Log`.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## Tâches  
  
|Pour|Consultez|  
|----------|---------------|  
|Écrire les informations sur l'événement dans les journaux de l'application.|[Comment : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Écrire les informations sur l'exception dans les journaux de l'application.|[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Écrire les informations de traçage dans les journaux de l'application au démarrage et à l'arrêt de l'application.|[Comment : enregistrer des messages lorsque l'application démarre ou s'arrête](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Configurer `My.Application.Log` pour écrire les informations dans un fichier texte.|[How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Configurer `My.Application.Log` pour écrire les informations dans un journal des événements.|[Comment : écrire dans le journal des événements de l'application](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Modifier l'emplacement où `My.Application.Log` écrit les informations.|[Procédure pas à pas : modification de l'emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Déterminer à quel emplacement `My.Application.Log` écrit les informations.|[Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|Créer un écouteur de journalisation personnalisé pour `My.Application.Log`.|[Walkthrough: Creating Custom Log Listeners](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|Filtrer la sortie des journaux `My.Application.Log`.|[Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Troubleshooting: Log Listeners](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)