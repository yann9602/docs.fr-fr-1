---
title: "Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3964551ba2eec0980541e95a7db20ef057a1dd61
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="7f80b-102">Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="7f80b-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="7f80b-103">Lorsque vous développez et distribuez des contrôles, vous pouvez que ces contrôles s’affichent dans le **choisir des éléments de boîte à outils** boîte de dialogue qui s’affiche lorsque vous cliquez sur le **boîte à outils** et sélectionnez  **Choisissez les éléments**.</span><span class="sxs-lookup"><span data-stu-id="7f80b-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="7f80b-104">Vous pouvez activer votre contrôle s’affiche dans cette boîte de dialogue à l’aide de la procédure d’inscription AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="7f80b-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="7f80b-105">Pour afficher votre contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="7f80b-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="7f80b-106">Installer votre assembly de contrôle dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="7f80b-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="7f80b-107">Pour plus d’informations, consultez [Comment : installer un Assembly dans le Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="7f80b-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="7f80b-108">- ou -</span><span class="sxs-lookup"><span data-stu-id="7f80b-108">-or-</span></span>  
  
-   <span data-ttu-id="7f80b-109">Inscrire votre contrôle et ses assemblys au moment du design associés à l’aide de la procédure d’inscription AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="7f80b-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="7f80b-110">AssemblyFoldersEx est un emplacement de Registre dans lequel stockent les chemins d’accès pour chaque version de l’infrastructure qu’ils prennent en charge des fournisseurs tiers.</span><span class="sxs-lookup"><span data-stu-id="7f80b-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="7f80b-111">Au moment du design résolution peut ressembler à cet emplacement de Registre pour rechercher des assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="7f80b-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="7f80b-112">Le script de Registre peut spécifier les contrôles que vous souhaitez voir apparaître dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="7f80b-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="7f80b-113">Pour plus d’informations, consultez [déploiement d’un contrôle personnalisé et des assemblys au moment du Design (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="7f80b-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f80b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f80b-114">See Also</span></span>  
 [<span data-ttu-id="7f80b-115">Choisir des éléments de boîte à outils, boîte de dialogue (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="7f80b-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="7f80b-116">Déploiement d’un contrôle personnalisé et des assemblys au moment du Design (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="7f80b-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="7f80b-117">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="7f80b-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="7f80b-118">Guide pratique pour installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="7f80b-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="7f80b-119">Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="7f80b-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
