---
title: "How to: Continue a Windows Service (Visual Basic) | Microsoft Docs"
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
  - "ServiceController.Continue"
helpviewer_keywords: 
  - "Windows Service applications, pausing"
  - "pausing Windows Service applications"
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 16
---
# How to: Continue a Windows Service (Visual Basic)
Cet exemple utilise le composant <xref:System.ServiceProcess.ServiceController> pour reprendre le service d'administration IIS sur l'ordinateur local.  
  
## Exemple  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Système d'exploitation Windows \> Services Windows**.  Pour plus d'informations, consultez [Extraits de code](../Topic/Code%20Snippets.md).  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   une référence de projet à System.serviceprocess.dll.  
  
-   l'accès aux membres de l'espace de noms <xref:System.ServiceProcess>.  Ajoutez une instruction `Imports` si vous n'utilisez pas des noms de membres qualifiés complets dans votre code.  Pour plus d'informations, consultez [Imports Statement \(.NET Namespace and Type\)](../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## Programmation fiable  
 Par défaut, la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> de la classe <xref:System.ServiceProcess.ServiceController> est l'ordinateur local.  Pour référencer des services Windows sur un autre ordinateur, modifiez la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> en lui affectant le nom de cet ordinateur.  
  
 Vous ne pouvez pas appeler la méthode <xref:System.ServiceProcess.ServiceController.Continue%2A> sur un service tant que le statut du contrôleur de services n'est pas <xref:System.ServiceProcess.ServiceControllerStatus>.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le service ne peut pas être repris.  \(<xref:System.InvalidOperationException>\)  
  
-   Une erreur s'est produite lors de l'accès à l'API système.  \(<xref:System.ComponentModel.Win32Exception>\)  
  
## Sécurité .NET Framework  
 Vous pouvez restreindre le contrôle des services disponibles sur l'ordinateur en utilisant <xref:System.ServiceProcess.ServiceControllerPermissionAccess> pour définir des autorisations dans la classe <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Vous pouvez restreindre l'accès aux informations sur les services en utilisant <xref:System.Security.Permissions.PermissionState> pour définir des autorisations dans la classe <xref:System.Security.Permissions.SecurityPermission>.  
  
## Voir aussi  
 <xref:System.ServiceProcess.ServiceController>   
 <xref:System.ServiceProcess.ServiceControllerStatus>   
 [How to: Pause a Windows Service \(Visual Basic\)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)