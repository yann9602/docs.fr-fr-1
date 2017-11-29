---
title: "Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms"
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
f1_keywords: TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c31998885926e9a7372bcf3182d1c95f0b79d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms
Windows Forms <xref:System.Windows.Forms.NotifyIcon> composant affiche une icône dans la zone de notification d’état de la barre des tâches. Pour afficher plusieurs icônes dans la zone d’état, vous devez avoir plusieurs <xref:System.Windows.Forms.NotifyIcon> composants sur votre formulaire. Pour définir l’icône affichée pour un contrôle, utilisez le <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriété. Vous pouvez également écrire du code le <xref:System.Windows.Forms.NotifyIcon.DoubleClick> afin que quelque chose se produit lorsque l’utilisateur double-clique sur l’icône du Gestionnaire d’événements. Par exemple, vous pouvez apporter à une boîte de dialogue s’affichent pour l’utilisateur de configurer le processus d’arrière-plan représenté par l’icône.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.NotifyIcon> composant est utilisé pour la notification uniquement, pour avertir les utilisateurs qu’une action ou un événement s’est produit ou une modification dans un état quelconque a eu lieu. Vous devez utiliser les menus, barres d’outils et autres éléments d’interface utilisateur pour l’interaction standard avec les applications.  
  
### <a name="to-set-the-icon"></a>Pour définir l’icône  
  
1.  Affecter une valeur à la <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriété. La valeur doit être de type `System.Drawing.Icon` et peut être chargé à partir d’un fichier .ico. Vous pouvez spécifier le fichier d’icône dans le code ou en cliquant sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté du <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriété dans le  **Propriétés** fenêtre, puis en sélectionnant le fichier dans le **ouvrir** boîte de dialogue qui s’affiche.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> la valeur `true`.  
  
3.  Définir le <xref:System.Windows.Forms.NotifyIcon.Text%2A> propriété à une chaîne d’info-bulle appropriée.  
  
     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’icône est la **Mes Documents** dossier. Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce dossier. Choix de cet emplacement permet également aux utilisateurs avec des niveaux d’accès système minimal d’exécuter en toute sécurité de l’application. L’exemple suivant nécessite un formulaire avec un <xref:System.Windows.Forms.NotifyIcon> contrôle déjà été ajouté. Elle requiert également un fichier icône nommé `Icon.ico`.  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [Guide pratique pour associer un menu contextuel à un composant NotifyIcon Windows Forms](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [NotifyIcon, composant](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [Vue d’ensemble du composant NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
