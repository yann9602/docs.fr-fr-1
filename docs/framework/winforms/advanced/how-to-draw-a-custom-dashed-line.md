---
title: "Comment : dessiner une ligne en pointillés personnalisée"
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
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 770ce290b21f7d0094a487c30079063b79a7c08d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Comment : dessiner une ligne en pointillés personnalisée
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]fournit plusieurs styles de ligne qui sont répertoriées dans le <xref:System.Drawing.Drawing2D.DashStyle> énumération. Si ces styles de ligne standard ne répondent pas à vos besoins, vous pouvez créer un modèle de tiret personnalisé.  
  
## <a name="example"></a>Exemple  
 Pour dessiner une ligne en pointillés personnalisée, placez les longueurs des tirets et des espaces dans un tableau et assignez le tableau comme valeur de la <xref:System.Drawing.Pen.DashPattern%2A> propriété d’un <xref:System.Drawing.Pen> objet. L’exemple suivant dessine une ligne en pointillés personnalisée basée sur le tableau `{5, 2, 15, 4}`. Si vous multipliez les éléments du tableau par la largeur du stylet 5, vous obtenez `{25, 10, 75, 20}`. Les tirets affichés longueur alternent entre 25 et 75, et les espaces alternent longueur comprise entre 10 et 20.  
  
 L’illustration suivante montre la ligne en pointillés résultante. Notez que le dernier tiret doit être inférieure à 25 unités afin que la ligne puisse terminer à (405, 5).  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un Windows Form et gérer du formulaire <xref:System.Windows.Forms.Control.Paint> événement. Collez le code précédent dans le <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
