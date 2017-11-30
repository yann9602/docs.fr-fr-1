---
title: Vue d'ensemble du composant HelpProvider (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42a788e44fde80662748e19a7244ce77bb26118f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="089d7-102">Vue d'ensemble du composant HelpProvider (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="089d7-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="089d7-103">Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) composant est utilisé pour associer un fichier d’aide HTML Help 1.x (fichier .chm généré par HTML Help Workshop ou fichier .htm) à votre application Windows.</span><span class="sxs-lookup"><span data-stu-id="089d7-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="089d7-104">Vous pouvez fournir une aide de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="089d7-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="089d7-105">Fournir une aide contextuelle pour les contrôles dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="089d7-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="089d7-106">Fournir une aide contextuelle sur une boîte de dialogue particulière ou sur certains contrôles sur une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="089d7-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="089d7-107">Ouvrez un fichier d’aide à des zones spécifiques, telles que la page principale d’une Table des matières, l’Index ou une fonction de recherche.</span><span class="sxs-lookup"><span data-stu-id="089d7-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="089d7-108">Utilisation du composant HelpProvider</span><span class="sxs-lookup"><span data-stu-id="089d7-108">Using the Help Provider</span></span>  
 <span data-ttu-id="089d7-109">Ajout d’un <xref:System.Windows.Forms.HelpProvider> composant à votre Windows Form permet aux autres contrôles sur le formulaire d’exposer les propriétés de l’aide de la <xref:System.Windows.Forms.HelpProvider> composant.</span><span class="sxs-lookup"><span data-stu-id="089d7-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="089d7-110">Cela vous permet de fournir une aide pour les contrôles sur votre Windows Form.</span><span class="sxs-lookup"><span data-stu-id="089d7-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="089d7-111">Vous pouvez associer un fichier d’aide avec le <xref:System.Windows.Forms.HelpProvider> à l’aide du composant le <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="089d7-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="089d7-112">Vous spécifiez le type d’aide fourni en appelant <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> et en fournissant une valeur à partir de la <xref:System.Windows.Forms.HelpNavigator> énumération pour le contrôle spécifié.</span><span class="sxs-lookup"><span data-stu-id="089d7-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="089d7-113">Vous fournissez le mot clé ou une rubrique d’aide en appelant le <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="089d7-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="089d7-114">Pour associer une chaîne d’aide spécifique à un autre contrôle, utilisez éventuellement la <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="089d7-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="089d7-115">La chaîne que vous associez à un contrôle à l’aide de cette méthode est affichée dans une fenêtre contextuelle lorsque l’utilisateur appuie sur la touche F1 pendant que le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="089d7-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="089d7-116">Si <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> n’a pas été défini, vous devez utiliser <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> pour fournir le texte d’aide.</span><span class="sxs-lookup"><span data-stu-id="089d7-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="089d7-117">Si vous avez défini les deux <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> et la chaîne d’aide, l’aide basée sur <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="089d7-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="089d7-118">Si vous rencontrez des problèmes en utilisant le chemin d’accès relatif lorsque spécifiant le chemin d’accès au fichier d’aide dans le <xref:System.Windows.Forms.Help.ShowHelp%2A> méthode ou <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriété de la <xref:System.Windows.Forms.HelpProvider> contrôle.</span><span class="sxs-lookup"><span data-stu-id="089d7-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="089d7-119">Par conséquent, veillez à utiliser le chemin d’accès absolu pour spécifier le fichier d’aide.</span><span class="sxs-lookup"><span data-stu-id="089d7-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089d7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="089d7-120">See Also</span></span>  
 [<span data-ttu-id="089d7-121">Systèmes d’aide dans les applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="089d7-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
