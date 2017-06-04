---
title: "Consid&#233;rations sur l&#39;h&#233;bergement d&#39;un contr&#244;le ActiveX dans un Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ActiveX (contrôles Windows Forms), ajouter"
  - "ActiveX (contrôles Windows Forms), héberger"
  - "contrôles Windows Forms, contrôles ActiveX"
  - "Windows Forms, contrôles ActiveX"
  - "Windows Forms, héberger des contrôles ActiveX"
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Consid&#233;rations sur l&#39;h&#233;bergement d&#39;un contr&#244;le ActiveX dans un Windows Form
Bien que les Windows Forms aient été optimisés pour l'hébergement de contrôles Windows Forms, il est toujours possible d'y inclure des contrôles ActiveX.  Prenez les éléments suivants en compte lors de la planification d'une application qui utilise des contrôles ActiveX :  
  
-   **Sécurité** Le Common Language Runtime a été optimisé sur le plan de la Sécurité d'Accès du Code.  Les applications recourant aux Windows Forms peuvent s'exécuter sans problème dans un environnement de niveau de confiance total et, dans un environnement de niveau de confiance partiel, avec la plupart des fonctionnalités disponibles.  L'hébergement des contrôles Windows Forms dans un navigateur ne présente aucun problème.  Toutefois, les contrôles ActiveX dans les Windows Forms ne peuvent pas tirer parti de ces améliorations de sécurité.  L'exécution d'un contrôle ActiveX requiert une autorisation de code non managé, définie avec la propriété <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=fullName>.  Pour plus d'informations sur la sécurité et l'autorisation de code non managé, consultez la classe [SecurityPermissionAttribute](frlrfSystemSecurityPermissionsSecurityPermissionAttributeClassTopic).  
  
-   **Coût total de propriété \(TCO, Total Cost of Ownership\)** Les contrôles ActiveX ajoutés à un Windows Form sont déployés sur ce Windows Form dans son intégralité, ce qui est susceptible d'accroître considérablement la taille du ou des fichiers créés.  En outre, l'utilisation de contrôles ActiveX sur des Windows Forms exige une écriture dans le Registre.  Les répercussions sur l'ordinateur de l'utilisateur sont donc plus grandes qu'avec des Windows Forms, qui ne nécessitent pas d'écriture dans le Registre.  
  
    > [!NOTE]
    >  L'utilisation d'un contrôle ActiveX requiert l'utilisation d'un wrapper COM Interop.  Pour plus d'informations, consultez [Interopérabilité COM en Visual Basic et Visual C\#](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md).  
  
    > [!NOTE]
    >  Si le nom d'un membre du contrôle ActiveX correspond à un nom défini dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], l'importateur de contrôles ActiveX fera précéder le nom du membre de **Ctl** lors de la création de la classe dérivée <xref:System.Windows.Forms.AxHost>.  Par exemple, si votre contrôle ActiveX comporte un membre nommé **Layout**, il est renommé **CtlLayout** dans la classe dérivée de AxHost, car l'événement **Layout** est défini dans [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## Voir aussi  
 [Comment : ajouter des contrôles ActiveX aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)   
 [Sécurité d'accès du code](../../../../docs/framework/misc/code-access-security.md)   
 [Controls and Programmable Objects Compared in Various Languages and Libraries](http://msdn.microsoft.com/fr-fr/021f2a1b-8247-4348-a5ad-e1d9ab23004b)   
 [Placement de contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)   
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)