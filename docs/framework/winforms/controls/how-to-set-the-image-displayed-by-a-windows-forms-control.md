---
title: "Comment : définir l'image affichée par un contrôle Windows Forms"
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
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d9f4d806b39e6e1272ddbb60befdaf8c76e46b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="dfdbb-102">Comment : définir l'image affichée par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dfdbb-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="dfdbb-103">Plusieurs contrôles Windows Forms peuvent afficher des images.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="dfdbb-104">Ces images peuvent être des icônes qui clarifier l’objectif de contrôle, comme une icône de disquette sur un bouton qui dénote le **enregistrer** commande.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="dfdbb-105">Les icônes peuvent également être des images d’arrière-plan pour donner au contrôle l’apparence et le comportement de que votre choix.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="dfdbb-106">Pour définir l’image affichée par un contrôle</span><span class="sxs-lookup"><span data-stu-id="dfdbb-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="dfdbb-107">Valeur du contrôle `Image` ou `BackgroundImage` propriété à un objet de type <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="dfdbb-108">En règle générale, vous chargez l’image à partir d’un fichier à l’aide de la <xref:System.Drawing.Image.FromFile%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="dfdbb-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="dfdbb-109">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est la **Mes images** dossier.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="dfdbb-110">La plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="dfdbb-111">Cela permet également aux utilisateurs avec des niveaux d’accès système minimal exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="dfdbb-112">L’exemple de code suivant requiert que vous disposez déjà d’un formulaire avec un <xref:System.Windows.Forms.PictureBox> contrôle ajouté.</span><span class="sxs-lookup"><span data-stu-id="dfdbb-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfdbb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfdbb-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
