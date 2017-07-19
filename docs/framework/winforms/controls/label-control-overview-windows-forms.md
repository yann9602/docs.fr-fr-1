---
title: "Vue d&#39;ensemble du contr&#244;le Label (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Label"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "images (Windows Forms), afficher dans les étiquettes"
  - "Label (contrôle Windows Forms), à propos du contrôle Label"
  - "étiquettes"
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du contr&#244;le Label (Windows Forms)
Le contrôle <xref:System.Windows.Forms.Label> Windows Forms permet d'afficher du texte ou des images qui ne peuvent pas être modifiés par l'utilisateur.  Il est utilisé pour identifier des objets sur un formulaire — pour décrire ce que fait un contrôle lorsque vous cliquez dessus, par exemple, ou pour afficher des informations en réponse à un événement ou à un processus d'exécution dans votre application.  Par exemple, vous pouvez utiliser des contrôles Label pour ajouter des légendes à des zones de texte, des zones de liste, des zones de liste déroulante, etc.  Vous pouvez également écrire du code qui modifie le texte affiché dans une étiquette en réponse à des événements survenant au moment de l'exécution.  Par exemple, si votre application prend plusieurs minutes pour traiter une opération, vous pouvez afficher dans l'étiquette un message indiquant que l'opération est en cours.  
  
## Utilisation du contrôle Label  
 Étant donné que le contrôle <xref:System.Windows.Forms.Label> ne peut pas recevoir le focus, vous pouvez également l'utiliser pour créer des touches d'accès rapide pour d'autres contrôles.  Une touche d'accès rapide permet à l'utilisateur de sélectionner l'autre contrôle en appuyant sur cette touche tout en maintenant la touche ALT enfoncée.  Pour plus d'informations, consultez [Création de touches d'accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).  
  
 La légende qui s'affiche dans l'étiquette est contenue dans la propriété <xref:System.Windows.Forms.Label.Text%2A>.  La propriété <xref:System.Windows.Forms.Label.TextAlign%2A> vous permet de définir l'alignement du texte dans l'étiquette.  Pour plus d'informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.Label>   
 [Comment : dimensionner un contrôle Label Windows Forms en fonction de son contenu](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)   
 [Comment : créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)