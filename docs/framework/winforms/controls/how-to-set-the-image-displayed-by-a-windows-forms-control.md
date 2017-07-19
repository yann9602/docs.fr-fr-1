---
title: "Comment&#160;: d&#233;finir l&#39;image affich&#233;e par un contr&#244;le Windows Forms | Microsoft Docs"
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
  - "bouton (contrôle Windows Forms), images"
  - "contrôles (Windows Forms), images"
  - "exemples (Windows Forms), contrôles"
  - "images (Windows Forms), contrôles Windows Forms"
  - "contrôles Windows Forms, images"
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;finir l&#39;image affich&#233;e par un contr&#244;le Windows Forms
Plusieurs contrôles Windows Forms peuvent afficher des images.  Ces images peuvent être des icônes qui explicitent le but du contrôle \(une icône de disquette sur un bouton qui désigne la commande **Enregistrer**, par exemple\).  Les icônes peuvent également être des images d'arrière\-plan destinées à donner au contrôle l'apparence et le comportement que vous souhaitez.  
  
### Pour définir l'image affichée par un contrôle  
  
1.  Affectez à la propriété `Image` ou `BackgroundImage` du contrôle un objet de type <xref:System.Drawing.Image>.  En général, vous chargez l'image à partir d'un fichier en utilisant la méthode <xref:System.Drawing.Image.FromFile%2A>.  
  
     Dans l'exemple de code suivant, le chemin d'accès défini pour l'emplacement de l'image est le dossier **Mes images**.  La plupart des ordinateurs qui exécutent le système d'exploitation Windows incluent ce répertoire.  Cela permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple de code suivant requiert un formulaire auquel un contrôle <xref:System.Windows.Forms.PictureBox> a été ajouté.  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## Voir aussi  
 <xref:System.Drawing.Image.FromFile%2A>   
 <xref:System.Drawing.Image>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>