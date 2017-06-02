---
title: "How to: Pause a Windows Service (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceController.Pause"
helpviewer_keywords: 
  - "Windows Service applications, pausing"
  - "pausing Windows Service applications"
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 15
---
# How to: Pause a Windows Service (Visual Basic)
Cet exemple utilise le composant <xref:System.ServiceProcess.ServiceController> pour interrompre le service d'administration IIS sur l'ordinateur local.  
  
## Exemple  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Système d'exploitation Windows \> Services Windows**.  Pour plus d'informations, consultez [Extraits de code](../Topic/Code%20Snippets.md).  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   une référence de projet à System.serviceprocess.dll.  
  
-   l'accès aux membres de l'espace de noms <xref:System.ServiceProcess>.  Ajoutez une instruction `Imports` si vous n'utilisez pas des noms de membres qualifiés complets dans votre code.  Pour plus d'informations, consultez [Imports Statement \(.NET Namespace and Type\)](../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## Programmation fiable  
 Par défaut, la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> de la classe <xref:System.ServiceProcess.ServiceController> est l'ordinateur local.  Pour référencer des services Windows sur un autre ordinateur, modifiez la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> en lui affectant le nom de cet ordinateur.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le service ne peut pas être interrompu.  \([classe InvalidOperationException](frlrfSystemInvalidOperationExceptionClassTopic)\).  
  
-   Une erreur s'est produite lors de l'accès à l'API système.  \([classe Win32Exception](frlrfSystemComponentModelWin32ExceptionClassTopic)\).  
  
## Sécurité .NET Framework  
 Vous pouvez restreindre le contrôle des services disponibles sur l'ordinateur en utilisant l'[énumération ServiceControllerPermissionAccess](frlrfSystemServiceProcessServiceControllerPermissionAccessClassTopic) pour définir des autorisations dans la [classe ServiceControllerPermission](frlrfSystemServiceProcessServiceControllerPermissionClassTopic).  
  
 Vous pouvez restreindre l'accès aux informations sur les services en utilisant l'[énumération PermissionState](frlrfSystemSecurityPermissionsPermissionStateClassTopic) pour définir des autorisations dans la [classe SecurityPermission](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic).  
  
## Voir aussi  
 <xref:System.ServiceProcess.ServiceController>   
 <xref:System.ServiceProcess.ServiceControllerStatus>   
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>   
 [How to: Continue a Windows Service \(Visual Basic\)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)