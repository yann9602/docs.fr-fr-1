---
title: "Résolution des problèmes : débogage des services Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="d04a8-102">Résolution des problèmes : débogage des services Windows</span><span class="sxs-lookup"><span data-stu-id="d04a8-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="d04a8-103">Lorsque vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagir.</span><span class="sxs-lookup"><span data-stu-id="d04a8-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="d04a8-104">Le **Service Manager** démarre votre service en appelant le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode), puis attend 30 secondes pour le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="d04a8-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="d04a8-105">Si la méthode ne retourne pas dans cette période, le gestionnaire affiche une erreur que le service ne peut pas être démarré.</span><span class="sxs-lookup"><span data-stu-id="d04a8-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="d04a8-106">Lorsque vous déboguez le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode décrite dans [Comment : déboguer des Applications de Service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), vous devez être conscient de ce délai de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="d04a8-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="d04a8-107">Si vous placez un point d’arrêt dans le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode) et ne pas à pas détaillé dans les 30 secondes, le gestionnaire ne démarre pas le service.</span><span class="sxs-lookup"><span data-stu-id="d04a8-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d04a8-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d04a8-108">See Also</span></span>  
 [<span data-ttu-id="d04a8-109">Guide pratique pour déboguer les applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="d04a8-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="d04a8-110">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="d04a8-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
