---
title: "Systèmes d’aide dans les applications Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b2f5d067d487bbd5b91576927aee21a9a44fde0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="62afa-102">Systèmes d’aide dans les applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="62afa-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="62afa-103">Un de le fournissiez plus importantes, comme un développeur d’applications, peut fournir à vos utilisateurs avec est un système d’aide.</span><span class="sxs-lookup"><span data-stu-id="62afa-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="62afa-104">Il s’agit où ils activera lorsqu’ils deviennent confondus ou désorientés.</span><span class="sxs-lookup"><span data-stu-id="62afa-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="62afa-105">En fournissant un système d’aide dans une application basée sur Windows est effectuée facilement à l’aide de la [HelpProvider, composant](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="62afa-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="62afa-106">Différents Types d’aide</span><span class="sxs-lookup"><span data-stu-id="62afa-106">Different Types of Help</span></span>  
 <span data-ttu-id="62afa-107">Le composant Windows Forms <xref:System.Windows.Forms.HelpProvider> sert à associer un fichier d'aide HTML Help 1.x (fichier .chm généré par HTML Help Workshop ou fichier .htm) à votre application Windows.</span><span class="sxs-lookup"><span data-stu-id="62afa-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="62afa-108">Le <xref:System.Windows.Forms.HelpProvider> composant peut être utilisé pour fournir une aide contextuelle pour les contrôles Windows Forms ou contrôles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="62afa-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="62afa-109">En outre, le <xref:System.Windows.Forms.HelpProvider> composant peut ouvrir un fichier d’aide à des zones spécifiques, telles que la page principale d’une table des matières, un index ou une fonction de recherche.</span><span class="sxs-lookup"><span data-stu-id="62afa-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="62afa-110">Pour des informations générales sur le <xref:System.Windows.Forms.HelpProvider> composant, consultez [vue d’ensemble du composant HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="62afa-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="62afa-111">Pour plus d’informations sur l’utilisation de la <xref:System.Windows.Forms.HelpProvider> composant pour afficher l’aide contextuelle dans les Windows Forms, consultez [Comment : afficher l’aide contextuelle](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="62afa-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="62afa-112">Pour plus d’informations sur l’utilisation de la <xref:System.Windows.Forms.ToolTip> composant pour afficher l’aide de contrôle spécifique, consultez [contrôle aide à l’aide des info-bulles](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span><span class="sxs-lookup"><span data-stu-id="62afa-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="62afa-113">Vous pouvez générer des fichiers d’aide HTML 1.x par HTML Help Workshop.</span><span class="sxs-lookup"><span data-stu-id="62afa-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="62afa-114">Pour plus d’informations sur HTML (aide), consultez « HTML Help Workshop » ou les autres rubriques « HTML Help » dans MSDN.</span><span class="sxs-lookup"><span data-stu-id="62afa-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62afa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62afa-115">See Also</span></span>  
 [<span data-ttu-id="62afa-116">Intégration de l’aide d’utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="62afa-116">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="62afa-117">HelpProvider, composant</span><span class="sxs-lookup"><span data-stu-id="62afa-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [<span data-ttu-id="62afa-118">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="62afa-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [<span data-ttu-id="62afa-119">Vue d'ensemble des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="62afa-119">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [<span data-ttu-id="62afa-120">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="62afa-120">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
