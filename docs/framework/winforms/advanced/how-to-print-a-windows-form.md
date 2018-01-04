---
title: "Comment : imprimer un Windows Form"
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
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c50b1f47d207334160ed12674ee8efb1390fb84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-windows-form"></a>Comment : imprimer un Windows Form
Dans le cadre du processus de développement, vous généralement souhaiterez imprimer une copie de votre Windows Form. L’exemple de code suivant montre comment imprimer une copie de l’écran actuel à l’aide de la <xref:System.Drawing.Graphics.CopyFromScreen%2A> (méthode).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Il s’agit d’un exemple de code complet qui contient un `Main` (méthode).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Vous n’avez pas l’autorisation d’accéder à l’imprimante.  
  
-   Aucune imprimante n’est installée.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour exécuter cet exemple de code, vous devez disposer d’autorisation d’accéder à l’imprimante que vous utilisez avec votre ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Guide pratique pour rendre des images avec GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [Comment : imprimer des graphiques dans Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
