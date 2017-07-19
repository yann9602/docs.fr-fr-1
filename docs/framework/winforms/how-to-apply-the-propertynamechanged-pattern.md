---
title: "Comment&#160;: appliquer le mod&#232;le PropertyNameChanged | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), modification des propriétés à l'aide du code"
  - "liaison de données, contrôles personnalisés"
  - "PropertyNameChanged (modèle), appliquer"
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: appliquer le mod&#232;le PropertyNameChanged
L'exemple de code suivant montre comment appliquer le modèle *NomPropriété*Changed à un contrôle personnalisé.  Appliquez ce modèle lorsque vous implémentez des contrôles personnalisés utilisés avec le moteur de liaison de données Windows Forms.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## Compilation du code  
 Pour compiler l'exemple de code précédent :  
  
-   Collez le code dans un fichier de code vide.  Vous devez utiliser le contrôle personnalisé sur un Windows Form contenant une méthode `Main`.  
  
## Voir aussi  
 [Comment : implémenter l'interface INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)   
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)