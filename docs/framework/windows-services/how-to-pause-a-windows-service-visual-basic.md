---
title: "Comment : interrompre un service Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 90f2b01fae057a05cc71f77cecea3fdf85c832b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="c6ab6-102">Comment : interrompre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6ab6-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="c6ab6-103">Cet exemple utilise le <xref:System.ServiceProcess.ServiceController> composant pour interrompre le service d’administration IIS sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6ab6-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6ab6-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="c6ab6-105">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c6ab6-106">Dans le sélecteur d’extraits de code, il se trouve dans **système d’exploitation Windows > Services Windows**.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="c6ab6-107">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c6ab6-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6ab6-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c6ab6-108">Compiling the Code</span></span>  
 <span data-ttu-id="c6ab6-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c6ab6-109">This example requires:</span></span>  
  
-   <span data-ttu-id="c6ab6-110">Une référence de projet à sur System.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="c6ab6-111">Un accès aux membres de l’espace de noms <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="c6ab6-112">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c6ab6-113">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c6ab6-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c6ab6-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="c6ab6-114">Robust Programming</span></span>  
 <span data-ttu-id="c6ab6-115">Le <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriété de la <xref:System.ServiceProcess.ServiceController> classe est l’ordinateur local par défaut.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="c6ab6-116">Pour référencer des services Windows sur un autre ordinateur, modifiez le <xref:System.ServiceProcess.ServiceController.MachineName%2A> nom à la propriété de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="c6ab6-117">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c6ab6-118">Le service ne peut pas être suspendu.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-118">The service cannot be paused.</span></span> <span data-ttu-id="c6ab6-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="c6ab6-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="c6ab6-120">Une erreur s'est produite lors de l'accès à une API système.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="c6ab6-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="c6ab6-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c6ab6-122">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6ab6-122">.NET Framework Security</span></span>  
 <span data-ttu-id="c6ab6-123">Contrôle des services sur l’ordinateur peut être restreinte à l’aide de la <xref:System.ServiceProcess.ServiceControllerPermissionAccess> pour définir les autorisations le <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="c6ab6-124">Accès aux informations de service peut être restreinte à l’aide de la <xref:System.Security.Permissions.PermissionState> pour définir les autorisations le <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="c6ab6-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ab6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6ab6-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="c6ab6-126">Guide pratique pour poursuivre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6ab6-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
