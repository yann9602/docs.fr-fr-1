---
title: "Comment : créer un pinceau plein, ou SolidBrush"
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
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 594d18d9607928b9a54a3b2639988775572f205c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-solid-brush"></a>Comment : créer un pinceau plein, ou SolidBrush
Cet exemple crée un <xref:System.Drawing.SolidBrush> objet qui peut être utilisé par un <xref:System.Drawing.Graphics> objet pour remplir les formes.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Une fois que vous avez terminé, vous devez appeler <xref:System.IDisposable.Dispose%2A> sur les objets qui consomment des ressources système, tels que les objets de pinceau.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.SolidBrush>  
 <xref:System.Drawing.Brush>  
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Pinceaux et remplissage de formes dans GDI+](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
