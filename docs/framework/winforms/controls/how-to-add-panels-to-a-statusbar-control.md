---
title: "Comment&#160;: ajouter des panneaux &#224; un contr&#244;le StatusBar | Microsoft Docs"
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
  - "panneaux, barres d'état"
  - "barres d'état, ajouter des panneaux"
  - "StatusBar (contrôle Windows Forms), ajouter des panneaux"
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: ajouter des panneaux &#224; un contr&#244;le StatusBar
> [!IMPORTANT]
>  Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> et y ajoutent des fonctionnalités ; toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 La zone programmable d'un contrôle [StatusBar, contrôle](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) se compose d'instances de la classe <xref:System.Windows.Forms.StatusBarPanel>.  Ces instances sont ajoutées par le biais d'additions à la classe <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
### Pour ajouter des panneaux à une barre d'état  
  
1.  Dans une procédure, créez des panneaux de barre d'état en les ajoutant à la collection <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  Configurez les propriétés des panneaux individuels en utilisant l'index passé par le biais de la propriété <xref:System.Windows.Forms.StatusBar.Panels%2A>.  
  
     Dans l'exemple de code suivant, le chemin d'accès défini pour l'emplacement de l'icône est le dossier **Mes documents**.  Cet emplacement est utilisé parce que la plupart des ordinateurs exécutant le système d'exploitation Windows incluent ce dossier.  Le choix de cet emplacement permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple suivant nécessite un formulaire auquel un contrôle <xref:System.Windows.Forms.StatusBar> a déjà été ajouté.  
  
    > [!NOTE]
    >  La collection <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> est une collection de base zéro, le code doit donc continuer en conséquence.  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =   
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image   
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [Collection Editor Dialog Box](http://msdn.microsoft.com/fr-fr/53fb3aad-bffa-4da5-ac89-8438e6fc803c)   
 [Comment : définir la taille des panneaux de la barre d'état](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)   
 [Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [Vue d'ensemble du contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)