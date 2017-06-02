---
title: "Comment&#160;: d&#233;finir une ic&#244;ne pour un bouton de barre d&#39;outils | Microsoft Docs"
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
  - "boutons (Windows Forms), icônes"
  - "exemples (Windows Forms), barres d'outils"
  - "icônes (Windows Forms), boutons de barre d'outils"
  - "images (Windows Forms), boutons de barre d'outils"
  - "ToolBar (contrôle Windows Forms), ajouter des icônes aux boutons"
  - "barres d'outils (Windows Forms), ajouter des icônes aux boutons"
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir une ic&#244;ne pour un bouton de barre d&#39;outils
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Les boutons <xref:System.Windows.Forms.ToolBar> sont capables d'afficher des icônes pour faciliter l'identification par les utilisateurs.  Pour cela, il faut ajouter des images au composant [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md), puis associer le composant <xref:System.Windows.Forms.ImageList> au contrôle <xref:System.Windows.Forms.ToolBar>.  
  
### Pour définir l'icône d'un bouton de barre d'outils par programme  
  
1.  Dans une procédure, instanciez un composant <xref:System.Windows.Forms.ImageList> et un contrôle <xref:System.Windows.Forms.ToolBar>.  
  
2.  Dans la même procédure, assignez une image au composant <xref:System.Windows.Forms.ImageList>.  
  
3.  Dans la même procédure, assignez le contrôle <xref:System.Windows.Forms.ImageList> au contrôle <xref:System.Windows.Forms.ToolBar> et assignez la propriété <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> de chaque bouton de barre d'outils.  
  
     Dans l'exemple de code suivant, le chemin d'accès défini pour l'emplacement de l'image est le dossier **Mes documents**.  La plupart des ordinateurs exécutant le système d'exploitation Windows disposent, en effet, de ce dossier.  Ceci permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple suivant suppose un formulaire auquel un contrôle <xref:System.Windows.Forms.PictureBox> a déjà été ajouté.  
  
     Si vous avez suivi les étapes ci\-dessus, votre code doit être similaire au code suivant.  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _   
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();   
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();   
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolBar>   
 [Comment : déclencher des événements de menu pour les boutons de barre d'outils](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)