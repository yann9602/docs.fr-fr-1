---
title: "Utilisation de conteneurs graphiques imbriqu&#233;s | Microsoft Docs"
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
  - "graphiques (Windows Forms), découper"
  - "graphiques, conteneurs imbriqués"
  - "graphiques, transformations dans les objets imbriqués"
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Utilisation de conteneurs graphiques imbriqu&#233;s
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit des conteneurs que vous pouvez utiliser pour remplacer ou augmenter temporairement une partie de l'état dans un objet <xref:System.Drawing.Graphics>.  Vous créez un conteneur en appelant la méthode <xref:System.Drawing.Graphics.BeginContainer%2A> d'un objet <xref:System.Drawing.Graphics>.  Vous pouvez appeler <xref:System.Drawing.Graphics.BeginContainer%2A> à plusieurs reprises pour constituer des conteneurs imbriqués.  Chaque appel à <xref:System.Drawing.Graphics.BeginContainer%2A> doit être conjugué à un appel à <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## Transformations dans les conteneurs imbriqués  
 L'exemple suivant crée un objet <xref:System.Drawing.Graphics> et un conteneur dans cet objet.  La transformation universelle de l'objet <xref:System.Drawing.Graphics> est une translation de 100 unités dans la direction x et de 80 unités dans la direction y.  La transformation universelle du conteneur est une rotation de trente degrés.  Le code effectue l'appel  `DrawRectangle(pen, -60, -30, 120, 60)`  deux fois.  Le premier appel à <xref:System.Drawing.Graphics.DrawRectangle%2A> est effectué à l'intérieur du conteneur, soit entre les appels à <xref:System.Drawing.Graphics.BeginContainer%2A> et <xref:System.Drawing.Graphics.EndContainer%2A>.  Le second appel à <xref:System.Drawing.Graphics.DrawRectangle%2A> est effectué après l'appel à <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Dans le code précédent, le rectangle dessiné à l'intérieur du conteneur est modifié d'abord par la transformation universelle du conteneur \(rotation\), puis par la transformation universelle de l'objet <xref:System.Drawing.Graphics> \(translation\).  Le rectangle dessiné à l'extérieur du conteneur est transformé uniquement par la transformation universelle de l'objet <xref:System.Drawing.Graphics> \(translation\).  L'illustration suivante montre les deux rectangles.  
  
 ![Conteneurs imbriqués](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## Découpage dans les conteneurs imbriqués  
 L'exemple suivant montre la façon dont les conteneurs imbriqués traitent les régions de découpage.  Le code crée un objet <xref:System.Drawing.Graphics> et un conteneur dans cet objet.  La région de découpage de l'objet <xref:System.Drawing.Graphics> est un rectangle et celle du conteneur une ellipse.  Le code fait deux appels à la méthode <xref:System.Drawing.Graphics.DrawLine%2A>.  Le premier appel à <xref:System.Drawing.Graphics.DrawLine%2A> est effectué à l'intérieur du conteneur et le deuxième appel à <xref:System.Drawing.Graphics.DrawLine%2A> à l'extérieur du conteneur \(après l'appel à <xref:System.Drawing.Graphics.EndContainer%2A>\).  Le premier trait est découpé par l'intersection des deux régions de découpage.  Le second trait est découpé par la région de découpage rectangulaire de l'objet <xref:System.Drawing.Graphics>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 L'illustration suivante montre les deux traits découpés.  
  
 ![Conteneur imbriqué](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 Comme dans les deux exemples précédents, les transformations et les régions de découpage se cumulent dans les conteneurs imbriqués.  Si vous définissez les transformations universelles du conteneur et de l'objet <xref:System.Drawing.Graphics>, les deux transformations s'appliqueront aux éléments dessinés à l'intérieur du conteneur.  La transformation du conteneur s'applique en premier, suivie de celle de l'objet <xref:System.Drawing.Graphics>.  Si vous définissez les régions de découpage du conteneur et de l'objet <xref:System.Drawing.Graphics>, les éléments dessinés à l'intérieur du conteneur seront découpés par l'intersection des deux régions de découpage.  
  
## Paramètres de qualité dans les conteneurs imbriqués  
 Les paramètres de qualité \(<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A> et équivalents\) des conteneurs imbriqués ne sont pas cumulatifs ; au contraire, les paramètres de qualité du conteneur remplacent temporairement les paramètres de qualité d'un objet <xref:System.Drawing.Graphics>.  Lorsque vous créez un conteneur, ses paramètres de qualité prennent les valeurs par défaut.  Supposez, par exemple, que vous disposiez d'un objet <xref:System.Drawing.Graphics> doté du mode de lissage <xref:System.Drawing.Drawing2D.SmoothingMode>.  Lorsque vous créez un conteneur, le mode lissage à l'intérieur du conteneur est celui par défaut.  Vous avez toute latitude pour définir le mode lissage du conteneur et tous les éléments dessinés dans le conteneur le seront tracés d'après votre sélection.  Les éléments dessinés après l'appel à <xref:System.Drawing.Graphics.EndContainer%2A> seront tracés en fonction du mode de lissage \(<xref:System.Drawing.Drawing2D.SmoothingMode>\) qui était en place avant l'appel à <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## Plusieurs couches de conteneurs imbriqués  
 Dans un objet <xref:System.Drawing.Graphics>, vous n'êtes pas limité à un conteneur.  Vous pouvez créer une séquence de conteneurs imbriqués les uns à la suite des autres et spécifier la transformation universelle, la région de découpage ainsi que les paramètres de qualité de chacun de ces conteneurs imbriqués.  Si vous appelez une méthode de dessin du conteneur le plus interne, les transformations seront appliquées dans l'ordre, à partir du conteneur le plus interne en passant par le conteneur le plus externe.  Les éléments dessinés dans le conteneur le plus interne seront découpés par l'intersection de toutes les régions de découpage.  
  
 L'exemple suivant crée un objet <xref:System.Drawing.Graphics> et affecte à sa propriété de restitution de texte la valeur <xref:System.Drawing.Drawing2D.SmoothingMode>.  Le code crée deux conteneurs imbriqués l'un dans l'autre.  La propriété de restitution de texte du conteneur externe a la valeur <xref:System.Drawing.Text.TextRenderingHint> tandis que celui du conteneur interne a la valeur <xref:System.Drawing.Drawing2D.SmoothingMode>.  Le code dessine trois chaînes : la première dans le conteneur interne, la seconde dans le conteneur externe et la dernière dans l'objet <xref:System.Drawing.Graphics> lui\-même.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 L'illustration suivante montre les trois chaînes.  Les chaînes dessinées dans le conteneur interne et dans l'objet <xref:System.Drawing.Graphics> sont lissées par l'anticrénelage.  La chaîne dessinée dans le conteneur externe n'est pas lissée par l'anticrénelage car la propriété <xref:System.Drawing.Graphics.TextRenderingHint%2A> a la valeur <xref:System.Drawing.Text.TextRenderingHint>.  
  
 ![Conteneurs imbriqués](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## Voir aussi  
 <xref:System.Drawing.Graphics>   
 [Gestion de l'état d'un objet graphique](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)