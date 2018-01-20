---
title: Guide pratique pour fournir de l'aide dans une application Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d23e5d5d19e17aedd37d4d5f6cbc41429463ddfb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="1864e-102">Guide pratique pour fournir de l'aide dans une application Windows</span><span class="sxs-lookup"><span data-stu-id="1864e-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="1864e-103">Vous pouvez utiliser le <xref:System.Windows.Forms.HelpProvider> composant pour attacher des rubriques d’aide d’un fichier d’aide à des contrôles spécifiques dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1864e-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="1864e-104">Le fichier d’aide peut être au format HTML, ou HTMLHelp 1.x ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="1864e-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1864e-105">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="1864e-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1864e-106">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="1864e-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1864e-107">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1864e-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="1864e-108">Pour fournir une aide</span><span class="sxs-lookup"><span data-stu-id="1864e-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="1864e-109">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.HelpProvider> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="1864e-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="1864e-110">Le composant sera placé dans la barre d’état en bas du Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1864e-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="1864e-111">Dans le **propriétés** , configurez le <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriété au fichier d’aide .chm, .col ou .htm.</span><span class="sxs-lookup"><span data-stu-id="1864e-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="1864e-112">Sélectionnez un autre contrôle, vous disposez sur votre formulaire et dans le **propriétés** , configurez le <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1864e-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="1864e-113">C’est la chaîne passée via le <xref:System.Windows.Forms.HelpProvider> composant à votre fichier d’aide pour appeler la rubrique d’aide appropriée.</span><span class="sxs-lookup"><span data-stu-id="1864e-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="1864e-114">Dans le **propriétés** , configurez la <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> propriété à une valeur de la <xref:System.Windows.Forms.HelpNavigator> énumération.</span><span class="sxs-lookup"><span data-stu-id="1864e-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="1864e-115">Ceci détermine la façon dont la propriété **HelpKeyword** est passée au système d’aide.</span><span class="sxs-lookup"><span data-stu-id="1864e-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="1864e-116">Le tableau suivant montre les paramètres possibles et leur description.</span><span class="sxs-lookup"><span data-stu-id="1864e-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="1864e-117">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="1864e-117">Member Name</span></span>|<span data-ttu-id="1864e-118">Description</span><span class="sxs-lookup"><span data-stu-id="1864e-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="1864e-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="1864e-119">AssociateIndex</span></span>|<span data-ttu-id="1864e-120">Spécifie que l’index d’une rubrique spécifiée est exécuté dans l’URL spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1864e-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="1864e-121">Find</span><span class="sxs-lookup"><span data-stu-id="1864e-121">Find</span></span>|<span data-ttu-id="1864e-122">Spécifie que la page de recherche d’une URL spécifiée est affichée.</span><span class="sxs-lookup"><span data-stu-id="1864e-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="1864e-123">Index</span><span class="sxs-lookup"><span data-stu-id="1864e-123">Index</span></span>|<span data-ttu-id="1864e-124">Spécifie que l’index d’une URL spécifiée est affiché.</span><span class="sxs-lookup"><span data-stu-id="1864e-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="1864e-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="1864e-125">KeywordIndex</span></span>|<span data-ttu-id="1864e-126">Spécifie un mot clé à rechercher et l’action à effectuer dans l’URL spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1864e-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="1864e-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="1864e-127">TableOfContents</span></span>|<span data-ttu-id="1864e-128">Spécifie que la table des matières du fichier d’aide HTML 1.0 est affiché.</span><span class="sxs-lookup"><span data-stu-id="1864e-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="1864e-129">Rubrique</span><span class="sxs-lookup"><span data-stu-id="1864e-129">Topic</span></span>|<span data-ttu-id="1864e-130">Spécifie que la rubrique référencée par l’URL spécifiée est affichée.</span><span class="sxs-lookup"><span data-stu-id="1864e-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="1864e-131">Au moment de l’exécution, en appuyant sur F1 lorsque le contrôle : dont vous avez défini le **HelpKeyword** et **HelpNavigator** propriétés : a le focus ouvre le fichier d’aide associé à ce <xref:System.Windows.Forms.HelpProvider> composant.</span><span class="sxs-lookup"><span data-stu-id="1864e-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="1864e-132">Actuellement, la propriété **HelpNamespace** prend en charge les fichiers d’aide dans les trois formats suivants : HTMLHelp 1.x, HTMLHelp 2.0 et HTML.</span><span class="sxs-lookup"><span data-stu-id="1864e-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="1864e-133">Vous pouvez ainsi définir la propriété **HelpNamespace** sur une adresse http://, comme une page web.</span><span class="sxs-lookup"><span data-stu-id="1864e-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="1864e-134">Dans ce cas, elle ouvre le navigateur par défaut à la page web avec la chaîne spécifiée dans la propriété **HelpKeyword** utilisée comme ancre.</span><span class="sxs-lookup"><span data-stu-id="1864e-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="1864e-135">L’ancre est utilisée pour accéder à une partie spécifique d’une page HTML.</span><span class="sxs-lookup"><span data-stu-id="1864e-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1864e-136">Prenez soin de vérifier toutes les informations envoyées par un client avant de les utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="1864e-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="1864e-137">Des utilisateurs malveillants peuvent tenter d’envoyer ou d’injecter un script exécutable, des instructions SQL ou un autre code.</span><span class="sxs-lookup"><span data-stu-id="1864e-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="1864e-138">Avant d’afficher une entrée utilisateur, de la stocker dans une base de données ou de l’utiliser, vérifiez qu’elle ne contient pas d’informations potentiellement dangereuses.</span><span class="sxs-lookup"><span data-stu-id="1864e-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="1864e-139">Une façon habituelle de le vérifier est d’utiliser une expression régulière pour rechercher des mots clés comme « SCRIPT » quand vous recevez une entrée d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1864e-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="1864e-140">Vous pouvez également utiliser le <xref:System.Windows.Forms.HelpProvider> composant pour afficher une aide contextuelle, même si vous avez configuré pour afficher les fichiers d’aide pour les contrôles de vos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1864e-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="1864e-141">Pour plus d’informations, consultez [Guide pratique pour afficher l’aide contextuelle](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="1864e-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1864e-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1864e-142">See Also</span></span>  
 [<span data-ttu-id="1864e-143">Guide pratique pour afficher l’aide contextuelle</span><span class="sxs-lookup"><span data-stu-id="1864e-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="1864e-144">Affichage sous forme d’info-bulles de l’aide relative aux contrôles</span><span class="sxs-lookup"><span data-stu-id="1864e-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="1864e-145">Intégration de l’aide d’utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1864e-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="1864e-146">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1864e-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
