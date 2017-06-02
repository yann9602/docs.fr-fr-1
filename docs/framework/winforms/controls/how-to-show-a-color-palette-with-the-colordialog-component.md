---
title: "Comment&#160;: afficher une palette de couleurs &#224; l&#39;aide du composant ColorDialog | Microsoft Docs"
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
  - "boîte de dialogue des couleurs, afficher les palettes de couleurs"
  - "palettes de couleurs, boîte de dialogue"
  - "palettes de couleurs, affichage dans le composant ColorDialog"
  - "Color (propriété)"
  - "ColorDialog (composant), afficher les palettes de couleurs"
  - "couleurs, permettre aux utilisateurs de sélectionner"
  - "couleurs, afficher les palettes"
  - "palettes, afficher la couleur"
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: afficher une palette de couleurs &#224; l&#39;aide du composant ColorDialog
Le composant [ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) affiche une palette de couleurs et retourne une propriété contenant la couleur sélectionnée par l'utilisateur.  
  
### Pour choisir une couleur à l'aide du composant ColorDialog  
  
1.  Affichez la boîte de dialogue à l'aide de la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
2.  Utilisez la propriété <xref:System.Windows.Forms.DialogResult> pour déterminer la façon dont la boîte de dialogue a été fermée.  
  
3.  Utilisez la propriété <xref:System.Windows.Forms.ColorDialog.Color%2A> du composant <xref:System.Windows.Forms.ColorDialog> pour définir la couleur choisie.  
  
     Dans l'exemple ci\-dessous, le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button> ouvre un composant <xref:System.Windows.Forms.ColorDialog>.  Lorsqu'une couleur est sélectionnée et que l'utilisateur clique sur **OK**, l'arrière\-plan du contrôle <xref:System.Windows.Forms.Button> adopte cette couleur.  Cet exemple suppose que votre formulaire contient un contrôle <xref:System.Windows.Forms.Button> et un composant <xref:System.Windows.Forms.ColorDialog>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog, composant](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)