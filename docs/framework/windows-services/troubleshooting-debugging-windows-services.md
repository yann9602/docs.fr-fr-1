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
ms.openlocfilehash: 51c28f6e9b6fa2974fb9861716b2c9fc2a38fe1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="45540-102">Résolution des problèmes : débogage des services Windows</span><span class="sxs-lookup"><span data-stu-id="45540-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="45540-103">Lorsque vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagir.</span><span class="sxs-lookup"><span data-stu-id="45540-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="45540-104">Le **Service Manager** démarre votre service en appelant le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode), puis attend 30 secondes pour le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retour de méthode.</span><span class="sxs-lookup"><span data-stu-id="45540-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="45540-105">Si la méthode ne retourne pas dans cette période, le gestionnaire affiche une erreur que le service ne peut pas être démarré.</span><span class="sxs-lookup"><span data-stu-id="45540-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="45540-106">Lorsque vous déboguez le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode décrite dans [Comment : déboguer des Applications de Service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), vous devez être conscient de ce délai de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="45540-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="45540-107">Si vous placez un point d’arrêt dans le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode) et ne pas à pas détaillé dans les 30 secondes, le gestionnaire ne démarre pas le service.</span><span class="sxs-lookup"><span data-stu-id="45540-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45540-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45540-108">See Also</span></span>  
 [<span data-ttu-id="45540-109">Comment : déboguer des Applications de Service Windows</span><span class="sxs-lookup"><span data-stu-id="45540-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="45540-110">Introduction aux Applications de Service Windows</span><span class="sxs-lookup"><span data-stu-id="45540-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
