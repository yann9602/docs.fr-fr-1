---
title: Transformations globales et locales
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
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e8d05bd0c3e76d643d56b652c8849eef1045ea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="global-and-local-transformations"></a>Transformations globales et locales
Une transformation globale est une transformation qui s’applique à tous les éléments dessinés par une donnée <xref:System.Drawing.Graphics> objet. En revanche, une transformation locale est une transformation qui s’applique à un élément spécifique doit être dessiné.  
  
## <a name="global-transformations"></a>Transformations globales  
 Pour créer une transformation globale, construisez un <xref:System.Drawing.Graphics> de l’objet et ensuite manipuler son <xref:System.Drawing.Graphics.Transform%2A> propriété. Le <xref:System.Drawing.Graphics.Transform%2A> propriété est un <xref:System.Drawing.Drawing2D.Matrix> objet, elle peut contenir n’importe quelle séquence de transformations affines. La transformation stockée dans le <xref:System.Drawing.Graphics.Transform%2A> propriété est appelée la transformation universelle. Le <xref:System.Drawing.Graphics> classe fournit plusieurs méthodes pour créer une transformation universelle composite : <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, et <xref:System.Drawing.Graphics.TranslateTransform%2A>. L’exemple suivant dessine une ellipse à deux reprises : une fois avant la création d’une transformation universelle et une fois après. La transformation tout d’abord mettre à l’échelle par un facteur de 0,5 dans la direction y, puis convertit 50 unités dans la direction x et puis pivote de 30 degrés.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 L’illustration suivante montre les matrices de cette transformation.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  Dans l’exemple précédent, l’ellipse autour de l’origine du système de coordonnées, qui se trouve à l’angle supérieur gauche de la zone cliente. Cela produit le même résultat que la rotation de l’ellipse autour de son propre centre.  
  
## <a name="local-transformations"></a>Transformations locales  
 Une transformation locale s’applique à un élément spécifique doit être dessiné. Par exemple, un <xref:System.Drawing.Drawing2D.GraphicsPath> objet a un <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> méthode qui vous permet de transformer les points de données de ce chemin d’accès. L’exemple suivant dessine un rectangle sans transformation et un chemin d’accès avec une transformation de rotation. (En supposant qu’il n’existe aucune transformation universelle).  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Vous pouvez combiner la transformation universelle avec des transformations locales pour atteindre une variété de résultats. Par exemple, vous pouvez utiliser la transformation universelle pour réviser le système de coordonnées et transformations locales pour faire pivoter et mettre à l’échelle des objets dessinés sur le nouveau système de coordonnées.  
  
 Supposons que vous souhaitiez un système de coordonnées qui a ses 200 pixels d’origine à partir du bord gauche de la zone cliente et à 150 pixels à partir du haut de la zone cliente. En outre, supposons que vous souhaitez que l’unité de mesure le pixel, avec l’axe des x pointant vers la droite et l’axe des y pointant vers le haut. Le système de coordonnées par défaut est l’axe des y pointant vers le bas, vous devez effectuer une réflexion sur l’axe horizontal. L’illustration suivante montre la matrice de ce type de réflexion.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Ensuite, supposons que vous devez effectuer une translation de 200 unités vers la droite et 150 unités vers le bas.  
  
 L’exemple suivant établit le système de coordonnées vient d’être décrit en définissant la transformation universelle d’un <xref:System.Drawing.Graphics> objet.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Le code suivant (placé à la fin de l’exemple précédent) crée un chemin d’accès qui se compose d’un rectangle avec son coin inférieur gauche à l’origine du nouveau système de coordonnées. Le rectangle est rempli qu’une seule fois sans transformation locale et une fois avec une transformation locale. La transformation locale se compose d’une mise à l’échelle horizontale par un facteur de 2 suivie d’une rotation de 30 degrés.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 L’illustration suivante montre le nouveau système de coordonnées et les deux rectangles.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Voir aussi  
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Utilisation des transformations dans GDI+ managé](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
