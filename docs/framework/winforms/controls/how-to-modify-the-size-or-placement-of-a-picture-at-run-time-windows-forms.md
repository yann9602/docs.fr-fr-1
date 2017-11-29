---
title: "Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution (Windows Forms)"
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
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution (Windows Forms)
Si vous utilisez Windows Forms <xref:System.Windows.Forms.PictureBox> contrôle sur un formulaire, vous pouvez définir le <xref:System.Windows.Forms.PictureBox.SizeMode%2A> propriété dessus pour :  
  
-   Aligner le coin supérieur gauche de l’image sur l’angle supérieur gauche du contrôle  
  
-   Centrer l’image dans le contrôle  
  
-   Ajuster la taille du contrôle en fonction de l’image que s’affiche  
  
-   Étirer une image, il affiche pour ajuster le contrôle  
  
 Étirer une image (en particulier un au format bitmap) peut entraîner une perte de qualité d’image. Métafichiers, qui sont des listes d’instructions graphiques destinées au dessin d’images au moment de l’exécution, sont mieux adaptées aux étirement que les bitmaps.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Pour définir la propriété SizeMode au moment de l’exécution  
  
1.  Définissez <xref:System.Windows.Forms.PictureBox.SizeMode%2A> à <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (la valeur par défaut), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>signifie que l’image est placée dans l’angle du coin supérieur gauche du contrôle ; Si l’image est plus grande que le contrôle, ses bords inférieurs et droit sont tronqués. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>signifie que l’image est centrée dans le contrôle ; Si l’image est plus grande que le contrôle, les bords extérieurs sont tronqués. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>signifie que la taille du contrôle est ajustée à la taille de l’image. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>est l’inverse et signifie que la taille de l’image est ajustée à la taille du contrôle.  
  
     Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement de l’image est le dossier Mes Documents. Pour cela, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire. Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité. L’exemple ci-dessous illustre un formulaire avec un <xref:System.Windows.Forms.PictureBox> contrôle déjà été ajouté.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.PictureBox>  
 [Guide pratique pour charger une image à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [Vue d’ensemble du contrôle PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Guide pratique pour définir des images au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox, contrôle](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
