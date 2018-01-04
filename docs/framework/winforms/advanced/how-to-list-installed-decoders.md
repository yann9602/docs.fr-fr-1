---
title: "Comment : répertorier les décodeurs installés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7993345a39a24c770fdd717580d428968dae836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-installed-decoders"></a>Comment : répertorier les décodeurs installés
Vous souhaiterez répertorier les décodeurs d’image disponibles sur un ordinateur, pour déterminer si votre application peut lire un format de fichier d’image spécifique. Le <xref:System.Drawing.Imaging.ImageCodecInfo> classe fournit le <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> méthodes statiques afin que vous pouvez déterminer quelle image décodeurs sont disponibles. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>Retourne un tableau de <xref:System.Drawing.Imaging.ImageCodecInfo> objets.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant génère la liste des décodeurs installés et leurs valeurs de propriété.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   une application Windows Forms ;  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour répertorier les encodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Utilisation d’encodeurs et de décodeurs d’images dans GDI+ managé](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
