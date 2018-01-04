---
title: "Comment : prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 415ffebbcf196a163932b1b83e32a6128f0bf1a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="8d5ee-102">Comment : prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog</span><span class="sxs-lookup"><span data-stu-id="8d5ee-102">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>
<span data-ttu-id="8d5ee-103">Vous pouvez résoudre les problèmes d’interopérabilité COM en affichant votre formulaire Windows sur une boucle de message [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], qui est créée en utilisant la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-103">You can resolve Component Object Model (COM) interoperability problems by displaying your Windows Form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which is created by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8d5ee-104">Pour qu’un formulaire fonctionne correctement à partir d’une application cliente COM, vous devez l’exécuter sur une boucle de messages Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-104">To make a form work correctly from a COM client application, you must run it on a Windows Forms message loop.</span></span> <span data-ttu-id="8d5ee-105">Pour cela, utilisez l'une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d5ee-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="8d5ee-106">Utilisez la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> pour afficher le formulaire Windows.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form;</span></span>  
  
-   <span data-ttu-id="8d5ee-107">Affichez chaque Windows Form sur un thread séparé.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-107">Display each Windows Form on a separate thread.</span></span> <span data-ttu-id="8d5ee-108">Pour plus d'informations, consultez [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span><span class="sxs-lookup"><span data-stu-id="8d5ee-108">For more information, see [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="8d5ee-109">Procédure</span><span class="sxs-lookup"><span data-stu-id="8d5ee-109">Procedure</span></span>  
 <span data-ttu-id="8d5ee-110">L’utilisation de la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> peut être le moyen le plus simple pour afficher un formulaire sur une boucle de messages [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] car, de toutes les approches, c’est elle qui nécessite le moins de code à implémenter.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-110">Using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method can be the easiest way to display a form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop because, of all the approaches, it requires the least code to implement.</span></span>  
  
 <span data-ttu-id="8d5ee-111">La méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> interrompt la boucle de messages de l’application non managée et affiche le formulaire comme une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-111">The <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method suspends the unmanaged application's message loop and displays the form as a dialog box.</span></span> <span data-ttu-id="8d5ee-112">Comme la boucle de messages de l’application hôte a été interrompue, la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> crée une nouvelle boucle de messages [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour traiter les messages du formulaire.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-112">Because the host application's message loop has been suspended, the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method creates a new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop to process the form's messages.</span></span>  
  
 <span data-ttu-id="8d5ee-113">L’inconvénient de l’utilisation de la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> est que le formulaire est ouvert comme boîte de dialogue modale.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-113">The disadvantage of using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method is that the form will be opened as a modal dialog box.</span></span> <span data-ttu-id="8d5ee-114">Ce comportement bloque toute interface utilisateur dans l’application appelante tant que le formulaire Windows est ouvert.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-114">This behavior blocks any user interface (UI) in the calling application while the Windows Form is open.</span></span> <span data-ttu-id="8d5ee-115">Quand l’utilisateur quitte le formulaire, la boucle de messages [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ferme la boucle et la boucle de messages antérieure de l’application reprend son exécution.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-115">When the user exits the form, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop closes and the earlier application's message loop starts running again.</span></span>  
  
 <span data-ttu-id="8d5ee-116">Vous pouvez créer une bibliothèque de classes dans Windows Forms qui a une méthode pour afficher le formulaire, puis créer la bibliothèque de classes pour COM interop.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-116">You can create a class library in Windows Forms which has a method to show the form, and then build the class library for COM interop.</span></span> <span data-ttu-id="8d5ee-117">Vous pouvez utiliser ce fichier DLL depuis Visual Basic 6.0 ou Microsoft Foundation Classes (MFC) et, depuis ces deux environnements, vous pouvez appeler la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> pour afficher le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8d5ee-117">You can use this DLL file from Visual Basic 6.0 or Microsoft Foundation Classes (MFC), and from either of these environments you can call the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the form.</span></span>  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="8d5ee-118">Pour prendre en charge COM Interop en affichant un formulaire Windows avec la méthode ShowDialog</span><span class="sxs-lookup"><span data-stu-id="8d5ee-118">To support COM interop by displaying a windows form with the ShowDialog method</span></span>  
  
-   <span data-ttu-id="8d5ee-119">Remplacez tous les appels à la méthode <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> par des appels à la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> dans votre composant [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d5ee-119">Replace all calls to the <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> method with calls to the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method in your [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5ee-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d5ee-120">See Also</span></span>  
 [<span data-ttu-id="8d5ee-121">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="8d5ee-121">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="8d5ee-122">Comment : prendre en charge l’interopérabilité COM en affichant chaque Windows Form sur son propre thread</span><span class="sxs-lookup"><span data-stu-id="8d5ee-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [<span data-ttu-id="8d5ee-123">Applications Windows Forms et non managées</span><span class="sxs-lookup"><span data-stu-id="8d5ee-123">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
