---
title: "Comment&#160;: &#233;crire dans le journal des &#233;v&#233;nements de l&#39;application (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Computer.EventLog (élément)"
  - "WriteEntry (méthode)"
  - "My.Computer.EventLog (élément)"
  - "journaux des événements, écrire dans"
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: &#233;crire dans le journal des &#233;v&#233;nements de l&#39;application (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour écrire des informations sur les événements qui se produisent dans votre application. Cet exemple montre comment configurer un écouteur de journalisation des événements pour que `My.Application.Log` écrive les informations de suivi dans le journal des événements de l’application.  
  
 Vous ne pouvez pas écrire dans le journal de sécurité. Pour pouvoir écrire dans le journal système, vous devez être membre du compte LocalSystem ou Administrateur.  
  
 Pour afficher un journal des événements, vous pouvez utiliser l’**Explorateur de serveurs** ou l’**Observateur d’événements Windows**. Pour plus d'informations, consultez [ETW Events in the .NET Framework](../Topic/ETW%20Events%20in%20the%20.NET%20Framework.md).  
  
> [!NOTE]
>  Les journaux des événements ne sont pas pris en charge sur Windows 95, Windows 98 ou Windows Millennium Edition.  
  
### Pour ajouter et configurer l’écouteur de journalisation des événements  
  
1.  Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et choisissez **Ouvrir**.  
  
     ou  
  
     S’il n’existe pas de fichier app.config :  
  
    1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
    2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier de configuration de l’application**.  
  
    3.  Cliquez sur **Ajouter**.  
  
2.  Recherchez la section `<listeners>` dans le fichier de configuration de l’application.  
  
     Vous pouvez trouver la section `<listeners>` dans la section `<source>` avec l’attribut de nom « DefaultSource », qui est imbriquée dans la section `<system.diagnostics>`, elle\-même imbriquée sous la section `<configuration>` de plus haut niveau.  
  
3.  Ajoutez cet élément à cette section `<listeners>` :  
  
    ```  
    <add name="EventLog"/>  
    ```  
  
4.  Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>`, dans la section `<configuration>` de plus haut niveau.  
  
5.  Ajoutez cet élément à cette section `<sharedListeners>` :  
  
    ```  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Remplacez `APPLICATION_NAME` par le nom de votre application.  
  
    > [!NOTE]
    >  En règle générale, une application écrit les erreurs seulement dans le journal des événements. Pour plus d’informations sur le filtrage de la sortie du journal, consultez [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### Pour écrire des informations sur les événements dans le journal des événements  
  
-   Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal des événements. Pour plus d’informations, consultez [Comment : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) et [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Une fois l’écouteur de journalisation des événements configuré pour un assembly, il reçoit tous les messages écrits par `My.Applcation.Log` depuis cet assembly.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)