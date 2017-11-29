---
title: "Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c772f547dc87af6618b92603ed1e709efc511b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="5c622-102">Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread</span><span class="sxs-lookup"><span data-stu-id="5c622-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="5c622-103">Vous pouvez résoudre les problèmes d'interopérabilité COM en affichant votre formulaire sur une boucle de message [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], que vous pouvez créer à l'aide de la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c622-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5c622-104">Pour qu'un Windows Form fonctionne correctement à partir d'une application cliente COM, vous devez l'exécuter sur une boucle de message Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5c622-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="5c622-105">Pour cela, utilisez l'une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c622-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="5c622-106">Utilisez la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> pour afficher le Windows Form.</span><span class="sxs-lookup"><span data-stu-id="5c622-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="5c622-107">Pour plus d'informations, consultez [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="5c622-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="5c622-108">Affichez chaque Windows Form sur un thread séparé.</span><span class="sxs-lookup"><span data-stu-id="5c622-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="5c622-109">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]propose une prise en charge étendue pour cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="5c622-109">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="5c622-110">Consultez également [Procédure pas à pas : prise en charge de COM Interop en affichant chaque Windows Forms sur son propre thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5c622-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c622-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c622-111">Example</span></span>  
 <span data-ttu-id="5c622-112">L'exemple de code suivant montre comment afficher le formulaire sur un thread distinct et appeler la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> pour démarrer une pompe de messages Windows Forms sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="5c622-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="5c622-113">Pour utiliser cette approche, vous devez marshaler tous les appels au formulaire à partir de l'application non managée à l'aide de la méthode <xref:System.Windows.Forms.Control.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="5c622-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="5c622-114">Cette approche exige que chaque instance d'un formulaire s'exécute sur son propre thread à l'aide de sa propre boucle de message.</span><span class="sxs-lookup"><span data-stu-id="5c622-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="5c622-115">Une seule boucle de message peut s'exécuter par thread.</span><span class="sxs-lookup"><span data-stu-id="5c622-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="5c622-116">Ainsi, vous ne pouvez pas modifier la boucle de message de l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="5c622-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="5c622-117">En revanche, vous pouvez modifier le composant [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour démarrer un nouveau thread qui utilise sa propre boucle de message.</span><span class="sxs-lookup"><span data-stu-id="5c622-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c622-118">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5c622-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="5c622-119">Compilez le types `COMForm`, `Form1`et `FormManager` dans un assembly nommé `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="5c622-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="5c622-120">Inscrivez l’assembly pour COM Interop en utilisant l’une des méthodes décrites dans [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="5c622-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="5c622-121">Vous pouvez maintenant utiliser l'assembly et son fichier de bibliothèque de types (.tlb) correspondant dans des applications non managées.</span><span class="sxs-lookup"><span data-stu-id="5c622-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="5c622-122">Par exemple, vous pouvez utiliser la bibliothèque de types comme référence dans un projet exécutable Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="5c622-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c622-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c622-123">See Also</span></span>  
 [<span data-ttu-id="5c622-124">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="5c622-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="5c622-125">Empaquetage d'un assembly pour COM</span><span class="sxs-lookup"><span data-stu-id="5c622-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [<span data-ttu-id="5c622-126">Inscription d’assemblys dans COM</span><span class="sxs-lookup"><span data-stu-id="5c622-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="5c622-127">Guide pratique pour prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog</span><span class="sxs-lookup"><span data-stu-id="5c622-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [<span data-ttu-id="5c622-128">Vue d'ensemble des applications Windows Forms et non managées</span><span class="sxs-lookup"><span data-stu-id="5c622-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
