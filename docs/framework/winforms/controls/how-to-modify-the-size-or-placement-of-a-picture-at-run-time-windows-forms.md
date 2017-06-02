---
title: "Comment&#160;: modifier la taille ou l&#39;emplacement d&#39;une image au moment de l&#39;ex&#233;cution (Windows Forms) | Microsoft Docs"
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
  - "exemples (Windows Forms), PictureBox (contrôle)"
  - "images (Windows Forms), contrôler la position dans le contrôle PictureBox (Windows Forms)"
  - "PictureBox (contrôle Windows Forms), alignement et taille d'image"
  - "images, contrôler la position dans le contrôle PictureBox (Windows Forms)"
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: modifier la taille ou l&#39;emplacement d&#39;une image au moment de l&#39;ex&#233;cution (Windows Forms)
Si vous utilisez le contrôle Windows Forms <xref:System.Windows.Forms.PictureBox> sur un formulaire, vous pouvez attribuer à sa propriété <xref:System.Windows.Forms.PictureBox.SizeMode%2A> la valeur suivante :  
  
-   aligner le coin supérieur gauche de l'image avec celui du contrôle ;  
  
-   centrer l'image dans le contrôle ;  
  
-   ajuster la taille du contrôle pour l'adapter à celle de l'image qu'il affiche ;  
  
-   étirer une image pour l'adapter à la taille du contrôle qu'elle contient.  
  
 L'étirement d'une image \(en particulier d'une image au format bitmap\) peut entraîner une dégradation de sa qualité.  Les métafichiers qui sont des listes d'instructions graphiques destinées au dessin d'images au moment de l'exécution, se prêtent mieux à l'étirement que les bitmaps.  
  
### Pour définir la propriété SizeMode au moment de l'exécution  
  
1.  Affectez à <xref:System.Windows.Forms.PictureBox.SizeMode%2A> la valeur <xref:System.Windows.Forms.PictureBoxSizeMode> \(valeur par défaut\), <xref:System.Windows.Forms.PictureBoxSizeMode>, <xref:System.Windows.Forms.PictureBoxSizeMode> ou <xref:System.Windows.Forms.PictureBoxSizeMode>.  <xref:System.Windows.Forms.PictureBoxSizeMode> signifie que l'image est placée dans l'angle supérieur gauche du contrôle ; si l'image est plus grande que le contrôle, ses bords droit et inférieur seront découpés.  <xref:System.Windows.Forms.PictureBoxSizeMode> signifie que l'image est centrée dans le contrôle ; si l'image est plus grande que le contrôle, les bords extérieurs de l'image seront découpés.  <xref:System.Windows.Forms.PictureBoxSizeMode> signifie que la taille du contrôle s'ajuste à la taille de l'image.  <xref:System.Windows.Forms.PictureBoxSizeMode> signifie l'inverse, c'est\-à\-dire que la taille de l'image s'ajuste à la taille du contrôle.  
  
     Dans l'exemple ci\-dessous, le chemin défini pour l'emplacement de l'image est le dossier Mes documents.  La plupart des ordinateurs exécutant le système d'exploitation Windows disposent, en effet, de ce dossier.  Ceci permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple suivant suppose un formulaire auquel un contrôle <xref:System.Windows.Forms.PictureBox> a déjà été ajouté.  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.PictureBox>   
 [Comment : charger une image à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)   
 [Vue d'ensemble du contrôle PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [Comment : définir des images au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)   
 [PictureBox, contrôle](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)