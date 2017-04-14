---
title: "Comment&#160;: d&#233;clencher des &#233;v&#233;nements de menu pour les boutons de barre d&#39;outils | Microsoft Docs"
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
  - "exemples (Windows Forms), barres d'outils"
  - "ToolBar (contrôle Windows Forms), gestionnaires d'événements Click"
  - "ToolBar (contrôle Windows Forms), coder les événements Click du bouton"
  - "barres d'outils (Windows Forms), gestionnaires d'événements Click"
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: d&#233;clencher des &#233;v&#233;nements de menu pour les boutons de barre d&#39;outils
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Si votre Windows Form contient un contrôle <xref:System.Windows.Forms.ToolBar> avec des boutons de barre d'outils, vous voudrez savoir sur quel bouton clique l'utilisateur.  
  
 Vous pouvez évaluer la propriété <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> de la classe <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> sur l'événement <xref:System.Windows.Forms.ToolBar.ButtonClick> du contrôle <xref:System.Windows.Forms.ToolBar>.  Dans l'exemple ci\-dessous, une boîte de message indiquant sur quel bouton l'utilisateur a cliqué s'affiche.  Pour plus d'informations, consultez [MessageBox, classe](frlrfSystemWindowsFormsMessageBoxClassTopic).  
  
 L'exemple ci\-dessous suppose qu'un contrôle <xref:System.Windows.Forms.ToolBar> a été ajouté à un Windows Form.  
  
### Pour prendre en charge l'événement Click dans une barre d'outils  
  
1.  Dans une procédure, ajoutez des boutons de barre d'outils au contrôle <xref:System.Windows.Forms.ToolBar>.  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
  
    ```  
  
    ```csharp  
    public void ToolBarConfig()   
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=   
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=   
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolBar.ButtonClick> du contrôle <xref:System.Windows.Forms.ToolBar>.  Utilisez une instruction switch Case et la classe <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> pour identifier le bouton de barre d'outils sur lequel l'utilisateur a cliqué.  En fonction du bouton identifié, affichez une boîte de message appropriée.  
  
    > [!NOTE]
    >  Une boîte de message est utilisée uniquement comme espace réservé dans cet exemple.  Vous pouvez ajouter du code supplémentaire à exécuter lorsque l'utilisateur clique sur les boutons de barre d'outils.  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolBar>   
 [Comment : ajouter des boutons à un contrôle ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)   
 [Comment : définir une icône pour un bouton de barre d'outils](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)