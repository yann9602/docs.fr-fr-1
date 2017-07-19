---
title: "Comment&#160;: cr&#233;er une interface utilisateur &#224; plusieurs volets avec des Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "interface utilisateur à plusieurs volets"
  - "SplitContainer (contrôle Windows Forms), utiliser le concepteur"
  - "interface utilisateur, à plusieurs volets"
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: cr&#233;er une interface utilisateur &#224; plusieurs volets avec des Windows Forms &#224; l&#39;aide du concepteur
Dans la procédure suivante, vous créerez une interface utilisateur à plusieurs volets qui est semblable à celle qui est utilisée dans Microsoft Outlook, avec une liste **Dossier**, un volet **Messages** et un volet **Aperçu**.  Cette disposition est obtenue principalement en ancrant des contrôles sur le formulaire.  
  
 Lorsque vous ancrez un contrôle, vous déterminez le bord du conteneur parent auquel un contrôle est attaché.  Par conséquent, si vous affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>, le bord droit du contrôle sera ancré au bord droit de son contrôle parent.  En outre, le bord ancré du contrôle est redimensionné pour correspondre à celui de son contrôle conteneur.  Pour plus d'informations sur le fonctionnement de la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A>, consultez [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Cette procédure se concentre sur la disposition du contrôle <xref:System.Windows.Forms.SplitContainer> et des autres contrôles sur le formulaire, et non sur l'ajout de fonctionnalités pour que l'application ressemble à Microsoft Outlook.  
  
 Pour créer cette interface utilisateur, vous placez tous les contrôles dans un contrôle <xref:System.Windows.Forms.SplitContainer> qui contient un contrôle <xref:System.Windows.Forms.TreeView> dans le panneau gauche.  Le panneau droit du contrôle <xref:System.Windows.Forms.SplitContainer> contient un deuxième contrôle <xref:System.Windows.Forms.SplitContainer> avec un contrôle <xref:System.Windows.Forms.ListView> au\-dessus d'un contrôle <xref:System.Windows.Forms.RichTextBox>.  Ces contrôles <xref:System.Windows.Forms.SplitContainer> permettent un redimensionnement indépendant des autres contrôles sur le formulaire.  Les techniques présentées dans cette procédure vous aideront à créer vos propres interfaces utilisateur personnalisées.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer une interface utilisateur du style Outlook au moment du design  
  
1.  Créez un projet d'application Windows.  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **Boîte à outils** jusqu'au formulaire.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.TreeView> de la **Boîte à outils** vers le panneau gauche du contrôle <xref:System.Windows.Forms.SplitContainer>.  Dans la fenêtre **Propriétés**, affectez la valeur <xref:System.Windows.Forms.DockStyle> à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> en cliquant sur le panneau gauche de l'éditeur de valeurs qui s'affiche lorsque vous cliquez sur la flèche vers le bas.  
  
4.  Faites glisser un autre contrôle <xref:System.Windows.Forms.SplitContainer> de la **Boîte à outils** ; placez\-le dans le panneau droit du contrôle <xref:System.Windows.Forms.SplitContainer> que vous avez ajouté à votre formulaire.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle> et à la propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A> la valeur <xref:System.Windows.Forms.Orientation>.  
  
5.  Faites glisser un contrôle <xref:System.Windows.Forms.ListView> de la **Boîte à outils** vers le panneau supérieur du deuxième contrôle <xref:System.Windows.Forms.SplitContainer> que vous avez ajouté à votre formulaire.  Affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> du contrôle <xref:System.Windows.Forms.ListView> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
6.  Faites glisser un contrôle <xref:System.Windows.Forms.RichTextBox> de la **Boîte à outils** vers le panneau inférieur du deuxième contrôle <xref:System.Windows.Forms.SplitContainer>.  Affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
     À ce stade, si vous appuyez sur F5 pour exécuter l'application, le formulaire affiche une interface utilisateur en trois parties, semblable à celle de Microsoft Outlook.  
  
    > [!NOTE]
    >  Lorsque vous placez le pointeur de souris sur l'un des séparateurs dans les contrôles <xref:System.Windows.Forms.SplitContainer>, vous pouvez modifier les dimensions internes.  
  
     À ce stade du développement de l'application, vous avez créé une interface utilisateur sophistiquée.  L'étape suivante consiste à continuer la programmation de l'application elle\-même, peut\-être en connectant le contrôle <xref:System.Windows.Forms.TreeView> et les contrôles <xref:System.Windows.Forms.ListView> à une source de données.  Pour plus d'informations sur la connexion de contrôles aux données, consultez [Liaison de données et Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)