---
title: "Comment&#160;: prendre en charge COM Interop en affichant un Windows Form avec la m&#233;thode ShowDialog | Microsoft Docs"
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
  - "COM (Windows Forms)"
  - "Windows Forms, non managé"
  - "COM interop, appel de méthodes"
  - "Contrôles ActiveX (Windows Forms), COM interop"
  - "ShowDialog (méthode)"
  - "Windows Forms, interopérabilité"
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: prendre en charge COM Interop en affichant un Windows Form avec la m&#233;thode ShowDialog
Vous pouvez résoudre les problèmes d’interopérabilité COM en affichant votre formulaire Windows sur une boucle de message [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], qui est créée en utilisant la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=fullName>.  
  
 Pour qu’un formulaire fonctionne correctement à partir d’une application cliente COM, vous devez l’exécuter sur une boucle de messages Windows Forms. Pour cela, utilisez l'une des approches suivantes :  
  
-   Utilisez la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> pour afficher le formulaire Windows.  
  
-   Affichez chaque Windows Form sur un thread séparé. Pour plus d'informations, consultez [Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## Procédure  
 L’utilisation de la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> peut être le moyen le plus simple pour afficher un formulaire sur une boucle de messages [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] car, de toutes les approches, c’est elle qui nécessite le moins de code à implémenter.  
  
 La méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> interrompt la boucle de messages de l’application non managée et affiche le formulaire comme une boîte de dialogue. Comme la boucle de messages de l’application hôte a été interrompue, la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> crée une nouvelle boucle de messages [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour traiter les messages du formulaire.  
  
 L’inconvénient de l’utilisation de la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> est que le formulaire est ouvert comme boîte de dialogue modale. Ce comportement bloque toute interface utilisateur dans l’application appelante tant que le formulaire Windows est ouvert. Quand l’utilisateur quitte le formulaire, la boucle de messages [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ferme la boucle et la boucle de messages antérieure de l’application reprend son exécution.  
  
 Vous pouvez créer une bibliothèque de classes dans Windows Forms qui a une méthode pour afficher le formulaire, puis créer la bibliothèque de classes pour COM interop. Vous pouvez utiliser ce fichier DLL depuis Visual Basic 6.0 ou Microsoft Foundation Classes \(MFC\) et, depuis ces deux environnements, vous pouvez appeler la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> pour afficher le formulaire.  
  
#### Pour prendre en charge COM Interop en affichant un formulaire Windows avec la méthode ShowDialog  
  
-   Remplacez tous les appels à la méthode <xref:System.Windows.Forms.Form.Show%2A?displayProperty=fullName> par des appels à la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=fullName> dans votre composant [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## Voir aussi  
 [Exposing .NET Framework Components to COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)   
 [Applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)