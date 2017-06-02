---
title: "Comment&#160;: ajouter des ic&#244;nes d&#39;application &#224; la barre des t&#226;ches &#224; l&#39;aide du composant NotifyIcon Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TrayIcon"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "icônes, ajouter à la barre des tâches"
  - "NotifyIcon (composant)"
  - "icônes de la zone d'état"
  - "barre des tâches, ajouter des icônes"
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: ajouter des ic&#244;nes d&#39;application &#224; la barre des t&#226;ches &#224; l&#39;aide du composant NotifyIcon Windows Forms
Le composant <xref:System.Windows.Forms.NotifyIcon> Windows Forms affiche une icône dans la zone de notification d'état de la barre des tâches.  Pour afficher plusieurs icônes, vous devez définir plusieurs composants <xref:System.Windows.Forms.NotifyIcon> dans votre formulaire.  Pour définir l'icône affichée pour un contrôle, utilisez la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.  Vous pouvez également écrire du code dans le gestionnaire d'événements <xref:System.Windows.Forms.NotifyIcon.DoubleClick> pour déclencher une action lorsque l'utilisateur double\-clique sur l'icône.  Par exemple, vous pouvez faire apparaître une boîte de dialogue permettant à l'utilisateur de configurer le processus d'arrière\-plan représenté par l'icône.  
  
> [!NOTE]
>  Le composant <xref:System.Windows.Forms.NotifyIcon> est utilisé pour la notification uniquement, pour informer les utilisateurs qu'une action ou un événement s'est produit, ou qu'un changement d'état quelconque a eu lieu.  Vous devez utiliser des menus, des barres d'outils et autres éléments d'interface utilisateur pour l'interaction standard avec les applications.  
  
### Pour définir l'icône  
  
1.  Assignez une valeur à la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.  Cette valeur doit être du type  `System.Drawing.Icon`  et peut être chargée à partir d'un fichier .ico.  Vous pouvez spécifier le fichier icône dans le code ou en cliquant sur le bouton Sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) en regard de la propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A> dans la fenêtre **Propriétés**, puis en sélectionnant le fichier dans la boîte de dialogue **Ouvrir** qui s'affiche.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> la valeur `true`.  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Text%2A> une chaîne d'info\-bulle appropriée.  
  
     Dans l'exemple de code suivant, le chemin d'accès défini pour l'emplacement de l'icône est le dossier **Mes documents**.  Cet emplacement est utilisé parce que la plupart des ordinateurs exécutant le système d'exploitation Windows incluent ce dossier.  Le choix de cet emplacement permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple suivant nécessite un formulaire auquel un contrôle <xref:System.Windows.Forms.NotifyIcon> a déjà été ajouté.  Il nécessite également un fichier icône nommé `Icon.ico`.  
  
     \[Visual Basic\]  
  
    ```  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
  
    ```  
  
     \[C\#\]  
  
    ```  
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
  
     \[cpp\]  
  
    ```  
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
  
## Voir aussi  
 <xref:System.Windows.Forms.NotifyIcon>   
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>   
 [Comment : associer un menu contextuel à un composant NotifyIcon Windows Forms](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)   
 [NotifyIcon, composant](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)   
 [Vue d'ensemble du composant NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)