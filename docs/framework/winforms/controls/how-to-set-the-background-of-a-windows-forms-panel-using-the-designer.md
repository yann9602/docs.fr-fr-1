---
title: "Comment&#160;: d&#233;finir l&#39;arri&#232;re-plan d&#39;un contr&#244;le Panel Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "couleurs d'arrière-plan, contrôles Panel Windows Forms"
  - "images d'arrière-plan, contrôles Panel Windows Forms"
  - "couleurs, contrôles Panel Windows Forms"
  - "Panel (contrôle Windows Forms), arrière-plan"
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;finir l&#39;arri&#232;re-plan d&#39;un contr&#244;le Panel Windows Forms &#224; l&#39;aide du concepteur
Un contrôle <xref:System.Windows.Forms.Panel> Windows Forms peut afficher une couleur et une image d'arrière\-plan.  La propriété <xref:System.Windows.Forms.Control.BackColor%2A> définit la couleur d'arrière\-plan pour les contrôles qui sont contenus dans le panneau, par exemple les étiquettes et cases d'option.  Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> n'est pas définie, la couleur <xref:System.Windows.Forms.Control.BackColor%2A> sélectionnée remplit tout le panneau.  Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> est définie, l'image est affichée derrière les contrôles qui sont contenus dans le panneau.  
  
 La procédure suivante nécessite un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.Panel>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir l'arrière\-plan dans le Concepteur Windows Forms  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.Panel>.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le bouton fléché situé en regard de la propriété <xref:System.Windows.Forms.Control.BackColor%2A> pour afficher une fenêtre à trois onglets.  
  
3.  Sélectionnez l'onglet **Personnaliser** pour afficher une palette de couleurs.  
  
4.  Sélectionnez l'onglet **Web** ou **System** pour afficher une liste de noms de couleurs prédéfinis, puis sélectionnez une couleur.  
  
5.  Dans la fenêtre **Propriétés**, cliquez sur le bouton fléché en regard de la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A>.  
  
6.  Dans la boîte de dialogue **Ouvrir**, sélectionnez le fichier que vous voulez afficher.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.BackColor%2A>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [Panel, contrôle](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Vue d'ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [Comment : grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)