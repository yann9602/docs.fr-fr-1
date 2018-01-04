---
title: "Utilisation de conteneurs graphiques imbriqués"
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
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 512c8903611f025364a1af2cb6cbaaffc8d759eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-nested-graphics-containers"></a>Utilisation de conteneurs graphiques imbriqués
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Fournit des conteneurs que vous pouvez utiliser pour remplacer ou augmenter la partie de l’état dans temporairement un <xref:System.Drawing.Graphics> objet. Vous créez un conteneur en appelant le <xref:System.Drawing.Graphics.BeginContainer%2A> méthode d’un <xref:System.Drawing.Graphics> objet. Vous pouvez appeler <xref:System.Drawing.Graphics.BeginContainer%2A> à plusieurs reprises pour former des conteneurs imbriqués. Chaque appel à <xref:System.Drawing.Graphics.BeginContainer%2A> doivent être associés à un appel à <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Transformations dans les conteneurs imbriqués  
 L’exemple suivant crée un <xref:System.Drawing.Graphics> objet et un conteneur dans ce <xref:System.Drawing.Graphics> objet. La transformation universelle de le <xref:System.Drawing.Graphics> l’objet est une translation 100 unités dans la direction x et 80 unités sur l’axe y. La transformation universelle du conteneur est une rotation de 30 degrés. Le code effectue l’appel `DrawRectangle(pen, -60, -30, 120, 60)` à deux reprises. Le premier appel à <xref:System.Drawing.Graphics.DrawRectangle%2A> se trouve dans le conteneur ; autrement dit, l’appel est entre les appels à <xref:System.Drawing.Graphics.BeginContainer%2A> et <xref:System.Drawing.Graphics.EndContainer%2A>. Le deuxième appel à <xref:System.Drawing.Graphics.DrawRectangle%2A> est après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Dans le code précédent, le rectangle dessiné à l’intérieur du conteneur est modifié d’abord par la transformation universelle du conteneur (rotation), puis par la transformation universelle de le <xref:System.Drawing.Graphics> objet (translation). Le rectangle dessiné à l’extérieur du conteneur est transformé uniquement par la transformation universelle de le <xref:System.Drawing.Graphics> objet (translation). L’illustration suivante montre les deux rectangles.  
  
 ![Imbriquée de conteneurs](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>Découpage dans les conteneurs imbriqués  
 L’exemple suivant montre les conteneurs imbriqués comment gérer les régions de découpage. Le code crée un <xref:System.Drawing.Graphics> objet et un conteneur dans ce <xref:System.Drawing.Graphics> objet. La zone de découpage de le <xref:System.Drawing.Graphics> l’objet est un rectangle, et la zone de découpage du conteneur une ellipse. Le code fait deux appels à la <xref:System.Drawing.Graphics.DrawLine%2A> (méthode). Le premier appel à <xref:System.Drawing.Graphics.DrawLine%2A> se trouve dans le conteneur et le deuxième appel à <xref:System.Drawing.Graphics.DrawLine%2A> est en dehors du conteneur (après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A>). La première ligne est découpée par l’intersection des deux régions de découpage. La deuxième ligne est découpée par la zone de découpage rectangulaire de la <xref:System.Drawing.Graphics> objet.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 L’illustration suivante montre les deux lignes ajustées.  
  
 ![Imbriqué conteneur](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 Comme le montrent les deux exemples précédents, les transformations et les régions de découpage sont cumulée dans les conteneurs imbriqués. Si vous définissez les transformations universelles du conteneur et le <xref:System.Drawing.Graphics> de l’objet, les deux transformations s’appliqueront aux éléments dessinés à l’intérieur du conteneur. La transformation du conteneur sera appliquée en premier et la transformation de la <xref:System.Drawing.Graphics> objet est ensuite appliqué. Si vous définissez les régions de découpage du conteneur et le <xref:System.Drawing.Graphics> de l’objet, éléments dessinés à l’intérieur du conteneur seront découpés par l’intersection de deux régions de découpage.  
  
## <a name="quality-settings-in-nested-containers"></a>Paramètres de qualité des conteneurs imbriqués  
 Paramètres de qualité (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>, etc.) dans les conteneurs imbriqués ne sont pas cumulatifs ; au lieu de cela, les paramètres de qualité du conteneur remplacent temporairement les paramètres de qualité d’un <xref:System.Drawing.Graphics> objet. Lorsque vous créez un nouveau conteneur, les paramètres de qualité pour ce conteneur sont définies les valeurs par défaut. Par exemple, supposons que vous ayez un <xref:System.Drawing.Graphics> objet avec le mode de lissage <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Lorsque vous créez un conteneur, le mode de lissage dans le conteneur est la valeur par défaut en mode de lissage. Vous êtes libre de définir le mode de lissage du conteneur et tous les éléments dessinés à l’intérieur du conteneur seront dessinés selon le mode que vous définissez. Les éléments dessinés après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A> seront dessinés en fonction du mode de lissage (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) qui était en vigueur avant l’appel à <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Plusieurs couches de conteneurs imbriqués  
 Vous n’êtes pas limité à un conteneur dans un <xref:System.Drawing.Graphics> objet. Vous pouvez créer une séquence de conteneurs, chacun imbriqués dans l’exemple précédent, et vous pouvez spécifier la transformation universelle, zone de découpage et les paramètres de qualité de chacun de ces conteneurs imbriqués. Si vous appelez une méthode de dessin du conteneur le plus interne, les transformations seront appliquées dans l’ordre, en commençant par le conteneur le plus interne et se terminant par le conteneur le plus éloigné. Les éléments dessinés dans le conteneur le plus interne seront découpés par l’intersection de toutes les zones de découpage.  
  
 L’exemple suivant crée un <xref:System.Drawing.Graphics> de l’objet et définit sa propriété de restitution de texte <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Le code crée deux conteneurs imbriqués dans l’autre. L’indicateur de rendu de texte du conteneur externe a la valeur <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, et l’indicateur de rendu de texte du conteneur interne est défini sur <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Le code dessine trois chaînes : un dans le conteneur interne, une dans le conteneur externe et l’autre à partir de la <xref:System.Drawing.Graphics> objet lui-même.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 L’illustration suivante montre les trois chaînes. Les chaînes dessinées dans le conteneur interne et à partir de la <xref:System.Drawing.Graphics> objet sont lissées par l’anticrénelage. La chaîne dessinée dans le conteneur externe n’est pas lissée par l’anticrénelage car la <xref:System.Drawing.Graphics.TextRenderingHint%2A> est définie sur <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Imbriquée de conteneurs](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Graphics>  
 [Gestion de l'état d'un objet graphique](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
