---
title: "Comment&#160;: cr&#233;er une zone de texte en lecture seule (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "lecture seule (zones de texte en)"
  - "zones de texte, en lecture seule"
  - "TextBox (contrôle Windows Forms), en lecture seule"
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er une zone de texte en lecture seule (Windows Forms)
Vous pouvez transformer une zone de texte Windows Forms modifiable en contrôle en lecture seule.  Par exemple, il se peut que la zone de texte affiche une valeur habituellement modifiable et cependant non modifiable actuellement en raison de l'état de l'application.  
  
### Pour créer une zone de texte en lecture seule  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur `true`.  La propriété ayant la valeur `true`, les utilisateurs peuvent toujours faire défiler et mettre le texte en surbrillance dans une zone de texte sans que les modifications ne soient permises.  La commande **Copier** est fonctionnelle dans une zone de texte, mais les commandes **Couper** et **Coller** ne le sont pas.  
  
    > [!NOTE]
    >  La propriété <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> affecte uniquement l'interaction utilisateur au moment de l'exécution.  Vous pouvez toujours modifier le contenu de la zone de texte par programme au moment de l'exécution en modifiant la propriété <xref:System.Windows.Forms.TextBox.Text%2A> de la zone de texte.  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [Comment : insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)