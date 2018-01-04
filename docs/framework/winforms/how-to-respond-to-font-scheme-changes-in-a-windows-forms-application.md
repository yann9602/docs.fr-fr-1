---
title: "Comment : répondre aux modifications de jeu de polices dans une application Windows Forms"
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
helpviewer_keywords: Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aac8d56c87ff03b313565a3d04cd3f3cc4e85f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="b16b1-102">Comment : répondre aux modifications de jeu de polices dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b16b1-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="b16b1-103">Dans les systèmes d’exploitation Windows, un utilisateur peut modifier les paramètres de police de l’échelle du système pour que la police par défaut s’affiche plus ou moins volumineux.</span><span class="sxs-lookup"><span data-stu-id="b16b1-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="b16b1-104">La modification de ces paramètres de police est critique pour les utilisateurs malvoyants et requièrent un type plus grand lire le texte à l’écran.</span><span class="sxs-lookup"><span data-stu-id="b16b1-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="b16b1-105">Vous pouvez ajuster votre application Windows Forms pour réagir à ces modifications en augmentant ou en réduisant la taille du formulaire et tous ses chaque fois que le jeu de polices change.</span><span class="sxs-lookup"><span data-stu-id="b16b1-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="b16b1-106">Si vous souhaitez que votre formulaire pour prendre en compte les modifications dans les tailles de police dynamiquement, vous pouvez ajouter le code à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="b16b1-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="b16b1-107">En règle générale, la police par défaut utilisée par les Windows Forms est la police retournée par le <xref:Microsoft.Win32> appel d’espace de noms à `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="b16b1-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="b16b1-108">La police retournée par cet appel change uniquement lorsque la résolution d’écran change.</span><span class="sxs-lookup"><span data-stu-id="b16b1-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="b16b1-109">Comme indiqué dans la procédure suivante, votre code doit modifier la police par défaut à <xref:System.Drawing.SystemFonts.IconTitleFont%2A> pour répondre aux modifications de taille de police.</span><span class="sxs-lookup"><span data-stu-id="b16b1-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="b16b1-110">Pour utiliser la police de bureau et répondre aux modifications de jeu de polices</span><span class="sxs-lookup"><span data-stu-id="b16b1-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="b16b1-111">Créer votre formulaire et les contrôles que vous souhaitez ajouter.</span><span class="sxs-lookup"><span data-stu-id="b16b1-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="b16b1-112">Pour plus d’informations, consultez [Comment : créer une Application Windows Forms à partir de la ligne de commande](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) et [contrôles à utiliser dans les Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b16b1-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="b16b1-113">Ajoutez une référence à la <xref:Microsoft.Win32> espace de noms à votre code.</span><span class="sxs-lookup"><span data-stu-id="b16b1-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="b16b1-114">Ajoutez le code suivant au constructeur de votre formulaire pour raccorder des gestionnaires d’événements requis et pour modifier la police par défaut en cours d’utilisation pour le formulaire.</span><span class="sxs-lookup"><span data-stu-id="b16b1-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="b16b1-115">Implémentez un gestionnaire pour le <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> événement qui provoque le formulaire à l’échelle automatiquement lorsque la <xref:Microsoft.Win32.UserPreferenceCategory.Window> changements de catégorie.</span><span class="sxs-lookup"><span data-stu-id="b16b1-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="b16b1-116">Enfin, implémentez un gestionnaire pour le <xref:System.Windows.Forms.Form.FormClosing> événement détache le <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b16b1-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b16b1-117">Échec d’inclure ce code met à votre application une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b16b1-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  <span data-ttu-id="b16b1-118">Compilez, puis exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="b16b1-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="b16b1-119">Pour modifier manuellement le jeu de polices dans Windows XP</span><span class="sxs-lookup"><span data-stu-id="b16b1-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="b16b1-120">Pendant l’exécution de votre application Windows Forms, cliquez sur le bureau Windows, puis choisissez **propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="b16b1-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b16b1-121">Dans le **propriétés d’affichage** boîte de dialogue, cliquez sur le **apparence** onglet.</span><span class="sxs-lookup"><span data-stu-id="b16b1-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="b16b1-122">À partir de la **la taille de police** liste déroulante, sélectionnez une nouvelle taille de police.</span><span class="sxs-lookup"><span data-stu-id="b16b1-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="b16b1-123">Vous remarquerez que le formulaire réagit maintenant pour exécuter ces modifications dans le jeu de polices de bureau.</span><span class="sxs-lookup"><span data-stu-id="b16b1-123">You will notice that the form now reacts to run time changes in the desktop font scheme.</span></span> <span data-ttu-id="b16b1-124">Lorsque l’utilisateur change entre **Normal**, **polices de grande taille**, et **très grands caractères**, le formulaire modifie la police et met à l’échelle correctement.</span><span class="sxs-lookup"><span data-stu-id="b16b1-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b16b1-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="b16b1-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="b16b1-126">Dans cet exemple de code, le constructeur contienne un appel à `InitializeComponent`, qui est défini lorsque vous créez un nouveau projet Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b16b1-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="b16b1-127">Supprimez cette ligne de code si vous générez votre application sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b16b1-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16b1-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b16b1-128">See Also</span></span>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [<span data-ttu-id="b16b1-129">Mise à l'échelle automatique dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b16b1-129">Automatic Scaling in Windows Forms</span></span>](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
