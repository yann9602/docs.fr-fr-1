---
title: "Comment : ajouter des contrôles sans interface utilisateur à des Windows Forms"
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
f1_keywords: NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abbf931cff9ad459e8c9221f91430ecccefa9cc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="e2891-102">Comment : ajouter des contrôles sans interface utilisateur à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="e2891-103">Un contrôle non visuel (ou un composant) fournit des fonctionnalités à votre application.</span><span class="sxs-lookup"><span data-stu-id="e2891-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="e2891-104">Contrairement à d’autres contrôles, les composants ne fournissent pas d’interface utilisateur à l’utilisateur et par conséquent, n’avez pas besoin être affiché sur l’aire du Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e2891-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="e2891-105">Lorsqu’un composant est ajouté à un formulaire, le Concepteur Windows Forms affiche une barre d’état redimensionnable au bas de l’écran où tous les composants sont affichés.</span><span class="sxs-lookup"><span data-stu-id="e2891-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="e2891-106">Une fois qu’un contrôle a été ajouté à la barre d’état du composant, vous pouvez sélectionner le composant et définissez ses propriétés comme vous le feriez pour tout autre contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e2891-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2891-107">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="e2891-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e2891-108">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="e2891-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e2891-109">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e2891-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="e2891-110">Pour ajouter un composant à un Windows Form</span><span class="sxs-lookup"><span data-stu-id="e2891-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="e2891-111">Ouvrez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e2891-111">Open the form.</span></span> <span data-ttu-id="e2891-112">Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="e2891-112">For details, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="e2891-113">Dans le **boîte à outils**, cliquez sur un composant et faites-le glisser vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="e2891-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="e2891-114">Votre composant s’affiche dans la barre d’état du composant.</span><span class="sxs-lookup"><span data-stu-id="e2891-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="e2891-115">En outre, les composants peuvent être ajoutés à un formulaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e2891-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="e2891-116">Il s’agit d’un scénario courant, en particulier, car les composants n’ont pas de représentation visuelle, contrairement aux contrôles qui ont une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2891-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="e2891-117">Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.Timer> composant est ajouté au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e2891-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="e2891-118">(Notez que [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] contient un numéro de différents types de minuteries ; dans ce cas, utilisez un Windows Forms <xref:System.Windows.Forms.Timer> composant.</span><span class="sxs-lookup"><span data-stu-id="e2891-118">(Note that [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="e2891-119">Pour plus d’informations sur les différentes minuteries dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], consultez [Introduction aux minuteurs serveur](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span><span class="sxs-lookup"><span data-stu-id="e2891-119">For more information about the different timers in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e2891-120">Composants ont souvent des propriétés spécifiques au contrôle qui doivent être définies pour le composant de fonctionner efficacement.</span><span class="sxs-lookup"><span data-stu-id="e2891-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="e2891-121">Dans le cas de la <xref:System.Windows.Forms.Timer> composant ci-dessous, vous définissez le `Interval` propriété.</span><span class="sxs-lookup"><span data-stu-id="e2891-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="e2891-122">Assurez-vous que, lors de l’ajout de composants à votre projet, définissez les propriétés nécessaires à ce composant.</span><span class="sxs-lookup"><span data-stu-id="e2891-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="e2891-123">Pour ajouter un composant à un Windows Form par programmation</span><span class="sxs-lookup"><span data-stu-id="e2891-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="e2891-124">Créez une instance de la <xref:System.Windows.Forms.Timer> classe dans le code.</span><span class="sxs-lookup"><span data-stu-id="e2891-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="e2891-125">Définir le `Interval` propriété pour déterminer l’intervalle entre les graduations de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="e2891-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="e2891-126">Configurez toutes les autres propriétés nécessaires pour votre composant.</span><span class="sxs-lookup"><span data-stu-id="e2891-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="e2891-127">Le code suivant illustre la création d’un <xref:System.Windows.Forms.Timer> avec son `Interval` jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="e2891-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e2891-128">Vous pouvez exposer votre ordinateur local à un risque de sécurité via le réseau en référençant un UserControl malveillant.</span><span class="sxs-lookup"><span data-stu-id="e2891-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="e2891-129">Il s’agit uniquement d’un problème dans le cas d’une personne malveillante, créer un contrôle personnalisé causer des dommages, suivi de vous ajouter par erreur à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e2891-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2891-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2891-130">See Also</span></span>  
 [<span data-ttu-id="e2891-131">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="e2891-132">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-132">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="e2891-133">Guide pratique pour ajouter des contrôles ActiveX aux Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-133">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="e2891-134">Guide pratique pour copier des contrôles entre des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-134">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [<span data-ttu-id="e2891-135">Placement de contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-135">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="e2891-136">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="e2891-137">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-137">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="e2891-138">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2891-138">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
