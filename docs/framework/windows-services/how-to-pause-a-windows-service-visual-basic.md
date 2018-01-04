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
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Comment : interrompre un service Windows (Visual Basic)
Cet exemple utilise le <xref:System.ServiceProcess.ServiceController> composant pour interrompre le service d’administration IIS sur l’ordinateur local.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **système d’exploitation Windows > Services Windows**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Une référence de projet à sur System.Diagnostics.dll.  
  
-   Un accès aux membres de l’espace de noms <xref:System.ServiceProcess>. Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriété de la <xref:System.ServiceProcess.ServiceController> classe est l’ordinateur local par défaut. Pour référencer des services Windows sur un autre ordinateur, modifiez le <xref:System.ServiceProcess.ServiceController.MachineName%2A> nom à la propriété de cet ordinateur.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le service ne peut pas être suspendu. (<xref:System.InvalidOperationException>)  
  
-   Une erreur s'est produite lors de l'accès à une API système. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Contrôle des services sur l’ordinateur peut être restreinte à l’aide de la <xref:System.ServiceProcess.ServiceControllerPermissionAccess> pour définir les autorisations le <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Accès aux informations de service peut être restreinte à l’aide de la <xref:System.Security.Permissions.PermissionState> pour définir les autorisations le <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [Guide pratique pour poursuivre un service Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
