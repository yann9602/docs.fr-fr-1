---
title: "Utilisation d'un pinceau à dégradé pour remplir des formes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a1c4ab7c2ee6f7164b6158dcb4ca4721be12650
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Utilisation d'un pinceau à dégradé pour remplir des formes
Vous pouvez utiliser un pinceau de dégradé pour remplir une forme avec une couleur. Par exemple, vous pouvez utiliser un dégradé horizontal pour remplir une forme avec une couleur qui change progressivement à mesure que vous déplacez le bord gauche de la forme sur le bord droit. Imaginez un rectangle avec un bord gauche noirs (représenté par les composants rouges, verts et bleus 0, 0, 0) et un bord droit de couleur rouge (représenté par 255, 0, 0). Si le rectangle est 256 pixels de large, le composant rouge d’un pixel donné sera supérieure à la composante rouge du pixel situé à sa gauche. Le pixel le plus à gauche dans une ligne a des composants de couleur (0, 0, 0), le deuxième pixel a (1, 0, 0), le troisième pixel (2, 0, 0) et ainsi de suite jusqu'à ce que vous obtenez au pixel plus à droite, ce qui a RVB (255, 0, 0). Ces valeurs de couleur interpolée composent le dégradé de couleur.  
  
 Un dégradé linéaire change de couleur quand vous déplacez horizontalement, verticalement ou parallèlement à une ligne inclinée spécifiée. Un dégradé de tracé change de couleur lorsque vous déplacez sur l’intérieur et la limite d’un chemin d’accès. Vous pouvez personnaliser les dégradés de chemin d’accès pour obtenir un large éventail d’effets.  
  
 L’illustration suivante montre un rectangle rempli avec un pinceau de dégradé linéaire et une ellipse remplie avec un pinceau de dégradé du chemin d’accès.  
  
 ![Dégradé](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer un dégradé linéaire](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 Montre comment créer un dégradé linéaire en utilisant la <xref:System.Drawing.Drawing2D.LinearGradientBrush> classe.  
  
 [Guide pratique pour créer un dégradé de tracé](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 Décrit comment créer un dégradé de chemin d’accès à l’aide la <xref:System.Drawing.Drawing2D.PathGradientBrush> classe.  
  
 [Guide pratique pour appliquer une correction gamma à un dégradé](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 Explique comment utiliser la correction gamma avec un pinceau de dégradé.  
  
## <a name="reference"></a>Référence  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Contient une description de cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Contient une description de cette classe et propose des liens vers tous ses membres.
