---
title: "Comment&#160;: d&#233;finir des images au moment de l&#39;ex&#233;cution (Windows Forms) | Microsoft Docs"
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
  - "bitmaps (Windows Forms), afficher dans le contrôle PictureBox (Windows Forms)"
  - "exemples (Windows Forms), PictureBox (contrôle)"
  - "images (Windows Forms), ajouter avec le contrôle PictureBox (Windows Forms)"
  - "PictureBox (contrôle Windows Forms), ajouter des images"
  - "PictureBox (contrôle Windows Forms), ajouter des images"
  - "images, définir l'affichage"
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir des images au moment de l&#39;ex&#233;cution (Windows Forms)
Vous pouvez définir par programme l'image affichée par un contrôle <xref:System.Windows.Forms.PictureBox> Windows Forms.  
  
### Pour définir une image par programme  
  
-   Définissez la propriété <xref:System.Windows.Forms.PictureBox.Image%2A> à l'aide de la méthode <xref:System.Drawing.Image.FromFile%2A> de la classe <xref:System.Drawing.Image>.  
  
     Dans l'exemple ci\-dessous, le chemin défini pour l'emplacement de l'image est le dossier Mes documents.  La plupart des ordinateurs exécutant le système d'exploitation Windows disposent, en effet, de ce dossier.  Ceci permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple suivant suppose un formulaire auquel un contrôle <xref:System.Windows.Forms.PictureBox> a déjà été ajouté.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### Pour effacer un graphisme  
  
-   Tout d'abord, libérez la mémoire utilisée par l'image, puis effacez le graphique.  Le garbage collection libère la mémoire ultérieurement si la gestion de la mémoire devient problématique.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  Pour plus d'informations sur les raisons pour lesquelles il est recommandé d'utiliser la méthode <xref:System.Drawing.Image.Dispose%2A> de cette façon, consultez [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).  
  
     Ce code efface l'image, et cela même si un graphisme a été chargé dans le contrôle au moment du design.  
  
## Voir aussi  
 <xref:System.Windows.Forms.PictureBox>   
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>   
 [Vue d'ensemble du contrôle PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [Comment : charger une image à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)   
 [Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)   
 [PictureBox, contrôle](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)