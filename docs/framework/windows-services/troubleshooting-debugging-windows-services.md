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
# <a name="troubleshooting-debugging-windows-services"></a>Résolution des problèmes : débogage des services Windows
Lorsque vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagir. Le **Service Manager** démarre votre service en appelant le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode), puis attend 30 secondes pour le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retour de méthode. Si la méthode ne retourne pas dans cette période, le gestionnaire affiche une erreur que le service ne peut pas être démarré.  
  
 Lorsque vous déboguez le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode décrite dans [Comment : déboguer des Applications de Service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), vous devez être conscient de ce délai de 30 secondes. Si vous placez un point d’arrêt dans le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode) et ne pas à pas détaillé dans les 30 secondes, le gestionnaire ne démarre pas le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déboguer des Applications de Service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Introduction aux Applications de Service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
