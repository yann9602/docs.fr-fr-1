---
title: "Comment&#160;: &#233;crire des param&#232;tres utilisateur au moment de l&#39;ex&#233;cution avec C# | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "paramètres d'application (Windows Forms), C#"
  - "paramètres d'application (Windows Forms), au moment de l'exécution"
  - "paramètres d'application (Windows Forms), écrire les paramètres utilisateur"
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: &#233;crire des param&#232;tres utilisateur au moment de l&#39;ex&#233;cution avec C# #
Les paramètres de portée application sont en lecture seule et ne peuvent être modifiés qu'au moment du design ou en modifiant le fichier .config entre les sessions d'application.  Les paramètres de portée utilisateur peuvent être écrits au moment de l'exécution tout comme vous modifieriez une valeur de propriété.  La nouvelle valeur est conservée pendant toute la durée de la session d'application.  Vous pouvez conserver les modifications apportées aux paramètres d'une session d'application à une autre en appelant la méthode Save.  
  
### Comment : écrire et conserver des paramètres utilisateur au moment de l'exécution avec C\#  
  
1.  Accédez au paramètre et attribuez\-lui une nouvelle valeur comme indiqué dans cet exemple :  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Si vous souhaitez conserver les modifications apportées aux paramètres d'une session d'application à l'autre, appelez la méthode Save comme indiqué dans cet exemple :  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Les paramètres utilisateur sont enregistrés dans un fichier dans un sous\-dossier du dossier de données d'application masqué local de l'utilisateur.  
  
## Voir aussi  
 [Utilisation de paramètres d'application et de paramètres utilisateur](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [Comment : lire des paramètres au moment de l'exécution avec C\#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)   
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)