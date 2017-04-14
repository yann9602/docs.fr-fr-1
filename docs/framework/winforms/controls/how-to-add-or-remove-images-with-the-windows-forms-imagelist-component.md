---
title: "Comment&#160;: ajouter ou supprimer des images avec le composant ImageList Windows Forms | Microsoft Docs"
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
  - "ImageList (composant Windows Forms), ajouter des images"
  - "ImageList (composant Windows Forms), supprimer des images"
  - "images (Windows Forms), ajouter au composant ImageList"
  - "images (Windows Forms), afficher avec les contrôles"
  - "images (Windows Forms), supprimer dans le composant ImageList"
  - "images (Windows Forms), stocker pour les contrôles"
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: ajouter ou supprimer des images avec le composant ImageList Windows Forms
Le composant <xref:System.Windows.Forms.ImageList> Windows Forms est habituellement rempli d'images avant d'être associé à un contrôle.  Toutefois, vous pouvez ajouter ou supprimer des images après que la liste d'images a été associée à un contrôle.  
  
> [!NOTE]
>  Lorsque vous supprimez des images, vérifiez que la propriété <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> de tous les contrôles associés est toujours valide.  
  
### Pour ajouter des images par programme  
  
-   Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ImageList.Images%2A> de la liste d'images.  
  
     Dans l'exemple de code suivant, le chemin d'accès défini pour l'emplacement de l'image est le dossier **Mes documents**.  La plupart des ordinateurs exécutant le système d'exploitation Windows disposent, en effet, de ce dossier.  Le choix de cet emplacement permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application avec plus de sécurité.  L'exemple de code suivant requiert un formulaire auquel un contrôle <xref:System.Windows.Forms.ImageList> a été ajouté.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### Pour ajouter des images avec une valeur de clé.  
  
-   Utilisez une des méthodes <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ImageList.Images%2A> de la liste d'images qui utilise une valeur de clé.  
  
     Dans l'exemple de code suivant, le chemin d'accès défini pour l'emplacement de l'image est le dossier **Mes documents**.  La plupart des ordinateurs exécutant le système d'exploitation Windows disposent, en effet, de ce dossier.  Le choix de cet emplacement permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application avec plus de sécurité.  L'exemple de code suivant requiert un formulaire auquel un contrôle <xref:System.Windows.Forms.ImageList> a été ajouté.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
  
```  
  
### Pour supprimer toutes les images par programme  
  
-   Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> pour supprimer une image.  
  
     \- ou \-  
  
     Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> pour effacer toutes les images de la liste.  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
  
```  
  
### Pour supprimer des images par clé  
  
-   Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> pour supprimer une image par sa clé.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
  
```  
  
## Voir aussi  
 [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)   
 [Vue d'ensemble du composant ImageList](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)   
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)