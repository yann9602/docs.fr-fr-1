---
title: "Comment : poursuivre un service Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 28dbbf2376416a340ad7853c026b2f763f695dcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="3b5d4-102">Comment : poursuivre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b5d4-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="3b5d4-103">Cet exemple utilise le <xref:System.ServiceProcess.ServiceController> composant pour continuer le service d’administration IIS sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b5d4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b5d4-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="3b5d4-105">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3b5d4-106">Dans le sélecteur d’extraits de code, il se trouve dans **système d’exploitation Windows > Services Windows**.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="3b5d4-107">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3b5d4-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b5d4-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3b5d4-108">Compiling the Code</span></span>  
 <span data-ttu-id="3b5d4-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3b5d4-109">This example requires:</span></span>  
  
-   <span data-ttu-id="3b5d4-110">Une référence de projet à sur System.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="3b5d4-111">Un accès aux membres de l’espace de noms <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="3b5d4-112">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="3b5d4-113">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="3b5d4-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3b5d4-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="3b5d4-114">Robust Programming</span></span>  
 <span data-ttu-id="3b5d4-115">Le <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriété de la <xref:System.ServiceProcess.ServiceController> classe est l’ordinateur local par défaut.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="3b5d4-116">Pour référencer des services Windows sur un autre ordinateur, modifiez le <xref:System.ServiceProcess.ServiceController.MachineName%2A> nom à la propriété de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="3b5d4-117">Vous ne pouvez pas appeler la <xref:System.ServiceProcess.ServiceController.Continue%2A> méthode sur un service jusqu'à ce que l’état du service contrôleur est <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="3b5d4-118">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3b5d4-119">Le service ne peut pas être repris.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-119">The service cannot be resumed.</span></span> <span data-ttu-id="3b5d4-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="3b5d4-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="3b5d4-121">Une erreur s'est produite lors de l'accès à une API système.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="3b5d4-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="3b5d4-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3b5d4-123">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b5d4-123">.NET Framework Security</span></span>  
 <span data-ttu-id="3b5d4-124">Contrôle des services sur l’ordinateur peut être restreinte à l’aide de la <xref:System.ServiceProcess.ServiceControllerPermissionAccess> pour définir des autorisations dans le <xref:System.ServiceProcess.ServiceControllerPermission> classe.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="3b5d4-125">Peut restreindre l’accès aux informations de service à l’aide de la <xref:System.Security.Permissions.PermissionState> pour définir des autorisations dans le <xref:System.Security.Permissions.SecurityPermission> classe.</span><span class="sxs-lookup"><span data-stu-id="3b5d4-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5d4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b5d4-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="3b5d4-127">Comment : suspendre un Service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b5d4-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
