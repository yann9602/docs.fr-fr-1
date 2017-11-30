---
title: "Comment : ajouter un écran de démarrage dans une application WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 973f35f6bfa259490a9423bf0b69d676ad968372
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="ba167-102">Comment : ajouter un écran de démarrage dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="ba167-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="ba167-103">Cette rubrique montre comment ajouter une fenêtre de démarrage, ou *écran de démarrage*, à une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ba167-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="ba167-104">Pour ajouter une image existante en tant qu’un écran de démarrage</span><span class="sxs-lookup"><span data-stu-id="ba167-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="ba167-105">Créez ou recherchez une image que vous souhaitez utiliser pour l’écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="ba167-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="ba167-106">Vous pouvez utiliser n’importe quel format d’image pris en charge par le composant WIC (Windows Imaging).</span><span class="sxs-lookup"><span data-stu-id="ba167-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="ba167-107">Par exemple, vous pouvez utiliser le format BMP, GIF, JPEG, PNG ou TIFF.</span><span class="sxs-lookup"><span data-stu-id="ba167-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="ba167-108">Ajoutez le fichier image au projet d’Application WPF.</span><span class="sxs-lookup"><span data-stu-id="ba167-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="ba167-109">Pour plus d’informations, consultez [NIB : Comment : ajouter des éléments existants à un projet](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="ba167-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="ba167-110">Dans l’Explorateur de solutions, sélectionnez l’image.</span><span class="sxs-lookup"><span data-stu-id="ba167-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="ba167-111">Dans la fenêtre Propriétés, cliquez sur la flèche déroulante pour le **Action de génération** propriété.</span><span class="sxs-lookup"><span data-stu-id="ba167-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="ba167-112">Sélectionnez **SplashScreen** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ba167-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba167-113">Si vous ne voyez pas le **SplashScreen** option, veillez à vérifier que vous utilisez [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ba167-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="ba167-114">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="ba167-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="ba167-115">Image de l’écran de démarrage s’affiche dans le centre de l’écran, puis disparaît lorsque la fenêtre principale de l’application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ba167-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="ba167-116">Pour supprimer l’écran de démarrage à partir d’une application</span><span class="sxs-lookup"><span data-stu-id="ba167-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="ba167-117">Dans l’Explorateur de solutions, sélectionnez l’image d’écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="ba167-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="ba167-118">Dans la fenêtre Propriétés, définissez la **Action de génération** à **aucun**.</span><span class="sxs-lookup"><span data-stu-id="ba167-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="ba167-119">Pour supprimer l’écran de démarrage à partir d’une application</span><span class="sxs-lookup"><span data-stu-id="ba167-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="ba167-120">Dans l’Explorateur de solutions, supprimez l’image d’écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="ba167-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="ba167-121">Excluez l’image d’écran de démarrage du projet.</span><span class="sxs-lookup"><span data-stu-id="ba167-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba167-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba167-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="ba167-123">NIB : Comment : ajouter des éléments existants à un projet</span><span class="sxs-lookup"><span data-stu-id="ba167-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
