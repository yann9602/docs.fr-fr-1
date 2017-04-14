---
title: "Comment&#160;: cr&#233;er des formulaires MDI parents | Microsoft Docs"
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
  - "MDI, créer des formulaires"
  - "formulaires parents"
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er des formulaires MDI parents
> [!IMPORTANT]
>  Cette rubrique utilise le contrôle <xref:System.Windows.Forms.MainMenu>, qui a été remplacé par le contrôle <xref:System.Windows.Forms.MenuStrip>.  Le contrôle <xref:System.Windows.Forms.MainMenu> est conservé pour la compatibilité descendante et une utilisation future, au besoin.  Pour plus d'informations sur la création d'un formulaire MDI parent à l'aide d'un <xref:System.Windows.Forms.MenuStrip>, consultez [Comment : créer une liste des fenêtres MDI avec MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Le formulaire MDI parent constitue la base d'une application d'interface multidocument \(MDI, Multiple\-Document Interface\).  Ce formulaire contient les fenêtres MDI enfants, c'est\-à\-dire les sous\-fenêtres dans lesquelles l'utilisateur interagit avec l'application MDI.  Il est facile de créer un formulaire MDI parent, que ce soit par programmation ou dans le Concepteur Windows Forms.  
  
### Pour créer un formulaire MDI parent au moment du design  
  
1.  Créez un projet d'application Windows.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété [IsMDIContainer](frlrfSystemWindowsFormsFormClassIsMDIContainerTopic) avec la valeur **true**.  
  
     Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.  
  
    > [!NOTE]
    >  Quand vous définissez les propriétés dans la fenêtre **Propriétés**, vous pouvez également choisir de définir la propriété `WindowState` avec la valeur **Maximized** pour agrandir le formulaire parent et faciliter ainsi la manipulation des fenêtres MDI enfants.  Sachez par ailleurs que le contour du formulaire MDI parent prend la couleur système \(définie dans le Panneau de configuration Système Windows\), et non la couleur d'arrière\-plan que vous avez définie avec la propriété <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=fullName>.  
  
3.  À partir de la **Boîte à outils**, faites glisser un contrôle **MenuStrip** sur le formulaire.  Créez un élément de menu de niveau supérieur en définissant la propriété **Text** avec la valeur **&File** et des éléments de sous\-menu appelés **&New** et **&Close**.  Créez également un menu de niveau supérieur appelé **&Window**.  
  
     Le premier menu crée et masque les éléments de menu au moment de l'exécution, alors que le deuxième menu garde la trace des fenêtres MDI enfants ouvertes.  À ce stade, vous avez créé une fenêtre MDI parente.  
  
4.  Appuyez sur **F5** pour exécuter l'application.  Pour plus d'informations sur la création de fenêtres MDI enfants qui opèrent dans un formulaire MDI parent, consultez [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).  
  
## Voir aussi  
 [Applications d'interface multidocument \(MDI, Multiple Document Interface\)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [Comment : déterminer l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [Comment : envoyer des données à l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [Comment : réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)