---
title: "Comment&#160;: lire des param&#232;tres au moment de l&#39;ex&#233;cution avec C# | Microsoft Docs"
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
  - "paramètres d'application (Windows Forms), lire"
  - "paramètres d'application (Windows Forms), au moment de l'exécution"
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: lire des param&#232;tres au moment de l&#39;ex&#233;cution avec C# #
Vous pouvez lire les paramètres de portée application et de portée utilisateur au moment de l'exécution via l'objet Propriétés.  L'objet Propriétés expose tous les paramètres par défaut du projet via le membre Properties.Settings.Default.  
  
### Pour lire des paramètres au moment de l'exécution avec C\#  
  
-   Accédez au paramètre approprié via le membre Properties.Settings.Default.  L'exemple suivant montre comment affecter un paramètre nommé `myColor` à une propriété BackColor.  Au préalable, vous devez avoir créé un fichier de paramètres contenant un paramètre nommé `myColor` de type `System.Drawing.Color`.  Pour plus d'informations sur la création d'un fichier de paramètres, consultez [Comment : créer un nouveau paramètre au moment du design](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## Voir aussi  
 [Utilisation de paramètres d'application et de paramètres utilisateur](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [Comment : écrire des paramètres utilisateur au moment de l'exécution avec C\#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)   
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)