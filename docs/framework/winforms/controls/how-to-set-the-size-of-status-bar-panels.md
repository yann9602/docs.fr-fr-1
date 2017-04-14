---
title: "Comment&#160;: d&#233;finir la taille des panneaux de la barre d&#39;&#233;tat | Microsoft Docs"
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
  - "panneaux, définir la taille dans les barres d'état"
  - "barres d'état, définir la taille d'un volet"
  - "StatusBar (contrôle Windows Forms), taille d'un volet"
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir la taille des panneaux de la barre d&#39;&#233;tat
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> remplace le contrôle <xref:System.Windows.Forms.StatusBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.StatusBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Chaque instance de la classe <xref:System.Windows.Forms.StatusBarPanel> d'un contrôle [StatusBar, contrôle](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) possède un certain nombre de propriétés dynamiques qui déterminent sa largeur et son comportement de redimensionnement au moment de l'exécution.  
  
### Pour définir la taille d'un panneau  
  
1.  Dans une procédure, définissez les propriétés <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A> et <xref:System.Windows.Forms.StatusBarPanel.Width%2A> \(ou tout sous\-ensemble de ces propriétés\) pour les panneaux de la barre d'état en utilisant leur index passé à la propriété <xref:System.Windows.Forms.StatusBar.Panels%2A> de la collection <xref:System.Windows.Forms.StatusBarPanel>.  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [Vue d'ensemble du contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)