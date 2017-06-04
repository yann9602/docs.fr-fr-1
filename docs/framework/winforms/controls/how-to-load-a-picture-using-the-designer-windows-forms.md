---
title: "Comment&#160;: charger une image &#224; l&#39;aide du concepteur (Windows Forms) | Microsoft Docs"
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
  - "formulaires, afficher des images"
  - "images (Windows Forms), afficher sur les Windows Forms"
  - "formats d'image"
  - "PictureBox (contrôle Windows Forms), ajouter des images"
  - "images, afficher"
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: charger une image &#224; l&#39;aide du concepteur (Windows Forms)
Le contrôle <xref:System.Windows.Forms.PictureBox> Windows Forms vous permet de charger et d'afficher une image dans un formulaire au moment du design en attribuant à la propriété <xref:System.Windows.Forms.PictureBox.Image%2A> une image valide.  Le tableau ci\-dessous répertorie les types de fichiers acceptables.  
  
|Type|Extension de nom de fichier|  
|----------|---------------------------------|  
|Bitmap|.bmp|  
|Icône|.ico|  
|GIF|.gif|  
|Métafichier|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour afficher une image au moment du design  
  
1.  Dessinez un contrôle <xref:System.Windows.Forms.PictureBox> dans un formulaire.  
  
2.  Dans la fenêtre Propriétés, sélectionnez la propriété <xref:System.Windows.Forms.PictureBox.Image%2A>, puis cliquez sur le bouton de sélection pour afficher la boîte de dialogue **Ouvrir**.  
  
3.  Si vous recherchez un type de fichier spécifique \(par exemple, .gif\), sélectionnez\-le dans la zone **Types de fichier**.  
  
4.  Sélectionnez le fichier à afficher.  
  
### Pour effacer une image au moment du design  
  
1.  Dans la fenêtre **Propriétés**, sélectionnez la propriété <xref:System.Windows.Forms.PictureBox.Image%2A> et cliquez avec le bouton droit sur l'image miniature affichée à gauche du nom de l'objet image.  Sélectionnez **Rétablir**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.PictureBox>   
 [Vue d'ensemble du contrôle PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)   
 [Comment : définir des images au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)   
 [PictureBox, contrôle](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)