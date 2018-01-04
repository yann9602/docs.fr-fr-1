---
title: "Comment : ajouter des contrôles ActiveX aux Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9328400917208dde9f81b493fbf26c6080dc9c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="02706-102">Comment : ajouter des contrôles ActiveX aux Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="02706-103">Alors que le Concepteur Windows Forms est optimisé pour héberger des contrôles Windows Forms, vous pouvez également insérer des contrôles ActiveX aux Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="02706-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="02706-104">Il existe des limitations de performances pour les Windows Forms lorsque des contrôles ActiveX leur sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="02706-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="02706-105">Avant d’ajouter des contrôles ActiveX à votre formulaire, vous devez les ajouter à la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="02706-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="02706-106">Pour plus d’informations, consultez [des composants COM, boîte de dialogue Personnaliser la boîte à outils](http://msdn.microsoft.com/en-us/171333f3-f207-4e02-bbdc-17862556212c).</span><span class="sxs-lookup"><span data-stu-id="02706-106">For more information, see [COM Components, Customize Toolbox Dialog Box](http://msdn.microsoft.com/en-us/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02706-107">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="02706-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="02706-108">Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="02706-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="02706-109">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="02706-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="02706-110">Pour ajouter un contrôle ActiveX à votre Windows Form</span><span class="sxs-lookup"><span data-stu-id="02706-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="02706-111">Double-cliquez sur le contrôle dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="02706-111">Double-click the control on the Toolbox.</span></span>  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="02706-112">Ajoute toutes les références au contrôle de votre projet.</span><span class="sxs-lookup"><span data-stu-id="02706-112"> adds all references to the control in your project.</span></span> <span data-ttu-id="02706-113">Pour plus d’informations sur les éléments à prendre en compte lors de l’utilisation de contrôles ActiveX aux Windows Forms, consultez [considérations sur l’hébergement d’un contrôle ActiveX dans un Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="02706-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02706-114">L’importateur de contrôles ActiveX Windows Forms (AxImp.exe) crée des arguments d’événement d’un type différent que prévu lors de l’importation de bibliothèques de liens dynamiques ActiveX.</span><span class="sxs-lookup"><span data-stu-id="02706-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="02706-115">Les arguments créés par AxImp.exe sont semblables à ce qui suit : `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, lorsque `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` est attendu.</span><span class="sxs-lookup"><span data-stu-id="02706-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="02706-116">N’oubliez pas que cette anomalie n’empêche pas le code de fonctionner normalement.</span><span class="sxs-lookup"><span data-stu-id="02706-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="02706-117">Pour plus d’informations, consultez [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="02706-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02706-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02706-118">See Also</span></span>  
 [<span data-ttu-id="02706-119">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="02706-120">Comparaison des contrôles et des objets programmables dans divers langages et bibliothèques</span><span class="sxs-lookup"><span data-stu-id="02706-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="02706-121">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="02706-122">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="02706-123">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="02706-124">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="02706-125">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02706-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
