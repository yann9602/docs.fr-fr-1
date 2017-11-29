---
title: "Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c772f547dc87af6618b92603ed1e709efc511b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Comment : prendre en charge l'interopérabilité COM en affichant chaque Windows Form sur son propre thread
Vous pouvez résoudre les problèmes d'interopérabilité COM en affichant votre formulaire sur une boucle de message [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], que vous pouvez créer à l'aide de la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>.  
  
 Pour qu'un Windows Form fonctionne correctement à partir d'une application cliente COM, vous devez l'exécuter sur une boucle de message Windows Forms. Pour cela, utilisez l'une des approches suivantes :  
  
-   Utilisez la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> pour afficher le Windows Form. Pour plus d'informations, consultez [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Affichez chaque Windows Form sur un thread séparé.  
  
 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]propose une prise en charge étendue pour cette fonctionnalité.  
  
 Consultez également [Procédure pas à pas : prise en charge de COM Interop en affichant chaque Windows Forms sur son propre thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment afficher le formulaire sur un thread distinct et appeler la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> pour démarrer une pompe de messages Windows Forms sur ce thread. Pour utiliser cette approche, vous devez marshaler tous les appels au formulaire à partir de l'application non managée à l'aide de la méthode <xref:System.Windows.Forms.Control.Invoke%2A> .  
  
 Cette approche exige que chaque instance d'un formulaire s'exécute sur son propre thread à l'aide de sa propre boucle de message. Une seule boucle de message peut s'exécuter par thread. Ainsi, vous ne pouvez pas modifier la boucle de message de l'application cliente. En revanche, vous pouvez modifier le composant [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour démarrer un nouveau thread qui utilise sa propre boucle de message.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Compilez le types `COMForm`, `Form1`et `FormManager` dans un assembly nommé `COMWinform.dll`. Inscrivez l’assembly pour COM Interop en utilisant l’une des méthodes décrites dans [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Vous pouvez maintenant utiliser l'assembly et son fichier de bibliothèque de types (.tlb) correspondant dans des applications non managées. Par exemple, vous pouvez utiliser la bibliothèque de types comme référence dans un projet exécutable Visual Basic 6.0.  
  
## <a name="see-also"></a>Voir aussi  
 [Exposition de composants .NET Framework à COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Empaquetage d'un assembly pour COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Inscription d’assemblys dans COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Guide pratique pour prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Vue d'ensemble des applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
