---
title: "Applications Windows Forms et non manag&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ActiveX (contrôles Windows Forms)"
  - "COM (Windows Forms)"
  - "COM Interop, Windows Forms"
  - "Windows Forms, interopérabilité"
  - "Windows Forms, non managés"
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Applications Windows Forms et non manag&#233;es
Les contrôles et les applications Windows Forms peuvent interagir avec des applications non managées, avec certaines restrictions.  Les sections suivantes décrivent les scénarios et les configurations pris en charge et non pris en charge par les applications et les contrôles Windows Forms.  
  
## Dans cette section  
 [Vue d'ensemble des applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Propose des informations générales sur l'utilisation et l'implémentation des contrôles Windows Forms qui fonctionnent avec les applications non managées.  
  
 [Comment : prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Fournit un exemple de code qui montre comment utiliser la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> pour exécuter un Windows Form dans une application non managée.  
  
 [Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Fournit un exemple de code qui montre comment exécuter un Windows Form sur son propre thread.  
  
 Consultez également [Procédure pas à pas : prise en charge de l'interopérabilité COM en affichant chaque Windows Form sur son propre thread](http://msdn.microsoft.com/library/ms233639%20\(v=vs.110\)).  
  
## Référence  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName>  
 Permet de créer un thread distinct pour un Windows Form.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=fullName>  
 Démarre une boucle de message pour un thread.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Marshale les appels à partir d'une application non managée vers un formulaire.  
  
## Rubriques connexes  
 [Exposing .NET Framework Components to COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Propose des informations générales sur l'utilisation de types .NET Framework dans les applications non managées.