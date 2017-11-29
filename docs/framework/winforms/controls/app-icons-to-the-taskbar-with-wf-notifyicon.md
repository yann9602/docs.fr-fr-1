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
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="163df-102">Comment : ajouter des icônes d’application à la barre des tâches à l’aide du composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="163df-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="163df-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> composant affiche une icône dans la zone de notification d’état de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="163df-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="163df-104">Pour afficher plusieurs icônes dans la zone d’état, vous devez avoir plusieurs <xref:System.Windows.Forms.NotifyIcon> composants sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="163df-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="163df-105">Pour définir l’icône affichée pour un contrôle, utilisez le <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="163df-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="163df-106">Vous pouvez également écrire du code le <xref:System.Windows.Forms.NotifyIcon.DoubleClick> afin que quelque chose se produit lorsque l’utilisateur double-clique sur l’icône du Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="163df-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="163df-107">Par exemple, vous pouvez apporter à une boîte de dialogue s’affichent pour l’utilisateur de configurer le processus d’arrière-plan représenté par l’icône.</span><span class="sxs-lookup"><span data-stu-id="163df-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="163df-108">Le <xref:System.Windows.Forms.NotifyIcon> composant est utilisé pour la notification uniquement, pour avertir les utilisateurs qu’une action ou un événement s’est produit ou une modification dans un état quelconque a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="163df-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="163df-109">Vous devez utiliser les menus, barres d’outils et autres éléments d’interface utilisateur pour l’interaction standard avec les applications.</span><span class="sxs-lookup"><span data-stu-id="163df-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="163df-110">Pour définir l’icône</span><span class="sxs-lookup"><span data-stu-id="163df-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="163df-111">Affecter une valeur à la <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="163df-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="163df-112">La valeur doit être de type `System.Drawing.Icon` et peut être chargé à partir d’un fichier .ico.</span><span class="sxs-lookup"><span data-stu-id="163df-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="163df-113">Vous pouvez spécifier le fichier d’icône dans le code ou en cliquant sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté du <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriété dans le  **Propriétés** fenêtre, puis en sélectionnant le fichier dans le **ouvrir** boîte de dialogue qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="163df-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2.  <span data-ttu-id="163df-114">Affectez à la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="163df-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="163df-115">Définir le <xref:System.Windows.Forms.NotifyIcon.Text%2A> propriété à une chaîne d’info-bulle appropriée.</span><span class="sxs-lookup"><span data-stu-id="163df-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="163df-116">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’icône est la **Mes Documents** dossier.</span><span class="sxs-lookup"><span data-stu-id="163df-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="163df-117">Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce dossier.</span><span class="sxs-lookup"><span data-stu-id="163df-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="163df-118">Choix de cet emplacement permet également aux utilisateurs avec des niveaux d’accès système minimal d’exécuter en toute sécurité de l’application.</span><span class="sxs-lookup"><span data-stu-id="163df-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="163df-119">L’exemple suivant nécessite un formulaire avec un <xref:System.Windows.Forms.NotifyIcon> contrôle déjà été ajouté.</span><span class="sxs-lookup"><span data-stu-id="163df-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="163df-120">Elle requiert également un fichier icône nommé `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="163df-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="163df-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="163df-121">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [<span data-ttu-id="163df-122">Guide pratique pour associer un menu contextuel à un composant NotifyIcon Windows Forms</span><span class="sxs-lookup"><span data-stu-id="163df-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [<span data-ttu-id="163df-123">NotifyIcon, composant</span><span class="sxs-lookup"><span data-stu-id="163df-123">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [<span data-ttu-id="163df-124">Vue d’ensemble du composant NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="163df-124">NotifyIcon Component Overview</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
