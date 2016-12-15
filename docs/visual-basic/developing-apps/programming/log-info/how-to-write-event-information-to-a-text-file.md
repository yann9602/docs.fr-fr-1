---
title: "How to: Write Event Information to a Text File (Visual Basic) | Microsoft Docs"
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
  - "event logs [Visual Studio], writing event information"
  - "text files, writing event information to a text file"
  - "events [Visual Basic], writing event information to a text file"
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Event Information to a Text File (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.  Cet exemple indique comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer les informations de traçage dans un fichier journal.  
  
### Pour ajouter et configurer l'écouteur de journalisation du fichier  
  
1.  Cliquez avec le bouton droit sur app.config dans l'**Explorateur de solutions** et sélectionnez l'option **Ouvrir**.  
  
     \- ou \-  
  
     S'il n'y a aucun fichier app.config :  
  
    1.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  
  
    2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier de configuration de l'application**.  
  
    3.  Cliquez sur **Ajouter**.  
  
2.  Recherchez la section `<listeners>` dans le fichier de configuration de l'application.  
  
     Vous trouverez la section \<écouteurs\> dans la section \<source\> portant l'attribut de nom "DefaultSource", qui est imbriquée dans la section \<system.diagnostics\> elle\-même imbriquée dans la section \<configuration\> de niveau supérieur.  
  
3.  Ajoutez cet élément à la section `<listeners>` :  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  Recherchez la section `<sharedListeners>` situé dans la section `<system.diagnostics>` imbriquée dans la section `<configuration>` de niveau supérieur.  
  
5.  Ajoutez cet élément à la section `<sharedListeners>` :  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Remplacez la valeur de l'attribut `customlocation` par le répertoire de journal.  
  
    > [!NOTE]
    >  Pour définir la valeur d'une propriété d'écouteur, utilisez un attribut qui porte le même nom que la propriété, toutes les lettres du nom étant en minuscule.  Par exemple, les attributs `location` et `customlocation` définissent les valeurs des propriétés <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> et <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.  
  
### Pour écrire des informations sur l'événement dans le journal de fichier  
  
-   Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal de fichier.  Pour plus d'informations, consultez [Comment : écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) et [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Une fois que l'écouteur de journalisation du fichier d'un assembly configuré, il reçoit tous les messages que `My.Application.Log` écrit à partir de cet assembly.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)