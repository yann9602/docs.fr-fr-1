---
title: "Comment&#160;: d&#233;terminer le panneau du contr&#244;le StatusBar Windows Forms sur lequel l&#39;utilisateur a cliqu&#233; | Microsoft Docs"
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
  - "Panel (contrôle Windows Forms), déterminer l'objet du clic"
  - "PanelClick (événement), déterminer le volet sur lequel l'utilisateur a cliqué"
  - "panneaux, déterminer un clic"
  - "barres d'état, déterminer le volet sur lequel l'utilisateur a cliqué"
  - "StatusBar (contrôle Windows Forms), coder les événements Click du volet"
  - "StatusBar (contrôle Windows Forms), déterminer le volet sur lequel l'utilisateur a cliqué"
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: d&#233;terminer le panneau du contr&#244;le StatusBar Windows Forms sur lequel l&#39;utilisateur a cliqu&#233;
> [!IMPORTANT]
>  Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> et y ajoutent des fonctionnalités ; toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 Pour programmer le contrôle [StatusBar, contrôle](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) pour répondre aux clics de l'utilisateur, utilisez une instruction case dans l'événement <xref:System.Windows.Forms.StatusBar.PanelClick>.  L'événement contient un argument \(l'argument panel\), qui contient une référence à l'objet <xref:System.Windows.Forms.StatusBarPanel> sur lequel le clic est effectué.  À l'aide de cette référence, vous pouvez identifier l'index du panneau sur lequel le clic est effectué et, par conséquent, le programme.  
  
> [!NOTE]
>  Vérifiez que la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> du contrôle <xref:System.Windows.Forms.StatusBar> a la valeur `true`.  
  
### Pour identifier le panneau sur lequel l'utilisateur a cliqué  
  
1.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.StatusBar.PanelClick>, utilisez une instruction `Select Case` \(dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\) ou `switch case` \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ou [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) pour identifier le panneau sur lequel l'utilisateur a cliqué en examinant l'index du panneau dans les arguments d'événement.  
  
     L'exemple de code suivant nécessite la présence dans le formulaire d'un contrôle <xref:System.Windows.Forms.StatusBar>, `StatusBar1`, et de deux objets <xref:System.Windows.Forms.StatusBarPanel>,`StatusBarPanel1`  et `StatusBarPanel2`.  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
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
  
## Voir aussi  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [Comment : définir la taille des panneaux de la barre d'état](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)   
 [Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [Vue d'ensemble du contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)