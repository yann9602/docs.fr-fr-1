---
title: "Comment&#160;: cr&#233;er une interface de style Explorateur Windows sur un Windows Form | Microsoft Docs"
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
  - "formulaires, type (Explorateur Windows)"
  - "SplitContainer (contrôle Windows Forms), Explorer-style (interface)"
  - "Explorateur Windows, créer avec Windows Forms"
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er une interface de style Explorateur Windows sur un Windows Form
L'Explorateur Windows est un choix d'interface utilisateur courant pour les applications en raison de son caractère familier.  
  
 L'Explorateur Windows consiste, essentiellement, en un contrôle <xref:System.Windows.Forms.TreeView> et un contrôle <xref:System.Windows.Forms.ListView> sur des panneaux séparés.  Les panneaux sont rendus redimensionnables par un séparateur.  Cette disposition des contrôles est très efficace pour l'affichage et l'exploration des informations.  
  
 Les étapes suivantes montrent comment disposer les contrôles dans un formulaire de type Explorateur Windows.  Elles ne montrent pas comment ajouter la fonctionnalité d'exploration des fichiers de l'application Explorateur Windows.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un formulaire Windows du style Explorateur Windows  
  
1.  Créez un projet d'application Windows.  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans la **Boîte à outils** :  
  
    1.  Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> sur votre formulaire.  
  
    2.  Faites glisser un contrôle <xref:System.Windows.Forms.TreeView> dans **SplitterPanel1** \(le panneau du contrôle <xref:System.Windows.Forms.SplitContainer> marqué **Panel1**\).  
  
    3.  Faites glisser un contrôle <xref:System.Windows.Forms.ListView> dans **SplitterPanel2** \(le panneau du contrôle <xref:System.Windows.Forms.SplitContainer> marqué **Panel2**\).  
  
3.  Sélectionnez les trois contrôles en appuyant sur la touche CTRL et en cliquant sur chacun d'eux.  Lorsque vous sélectionnez le contrôle <xref:System.Windows.Forms.SplitContainer>, cliquez sur la barre de fractionnement, plutôt que sur les panneaux.  
  
    > [!NOTE]
    >  N'utilisez pas la commande **Sélectionner tout** du menu **Edition**.  Si vous l'utilisez, la propriété requise à l'étape suivante n'apparaîtra pas dans la fenêtre **Propriétés**.  
  
4.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
5.  Appuyez sur F5 pour exécuter l'application.  
  
     Le formulaire affiche une interface utilisateur en deux parties rappelant celle de l'Explorateur Windows.  
  
    > [!NOTE]
    >  Lorsque vous faites glisser le séparateur, les panneaux se redimensionnent.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 [Comment : créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)   
 [Comment : définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)   
 [Comment : fractionner une fenêtre horizontalement](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)   
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)