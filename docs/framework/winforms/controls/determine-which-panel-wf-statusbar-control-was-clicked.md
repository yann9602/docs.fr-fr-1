---
title: "Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a91ad8c28bae7d517a9e13937d5de340b1b6a605
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué
> [!IMPORTANT]
>  Le <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> contrôles remplacer et ajouter des fonctionnalités à la <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôle ; Toutefois, le <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôles sont conservés pour la compatibilité descendante et l’utilisation future si vous Choisissez.  
  
 Programme le [contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) contrôle pour répondre aux clics de l’utilisateur, utilisez une instruction case dans la <xref:System.Windows.Forms.StatusBar.PanelClick> événement. L’événement contient un argument (l’argument panel), qui contient une référence à le clic sur <xref:System.Windows.Forms.StatusBarPanel>. À l’aide de cette référence, vous pouvez déterminer l’index du panneau et programmer en conséquence.  
  
> [!NOTE]
>  Vérifiez que le <xref:System.Windows.Forms.StatusBar> du contrôle <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> est définie sur `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Pour déterminer l’utilisateur a cliqué sur le panneau de configuration  
  
1.  Dans le <xref:System.Windows.Forms.StatusBar.PanelClick> Gestionnaire d’événements, utilisez un `Select Case` (dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) ou `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ou [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) pour déterminer le panneau a été utilisé en examinant l’index du panneau dans les arguments d’événement.  
  
     L’exemple de code suivant nécessite la présence, dans le formulaire, d’un <xref:System.Windows.Forms.StatusBar> (contrôle), `StatusBar1`et deux <xref:System.Windows.Forms.StatusBarPanel> objets, `StatusBarPanel1` et `StatusBarPanel2`.  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Guide pratique pour définir la taille des panneaux de la barre d'état](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [Vue d’ensemble du contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
