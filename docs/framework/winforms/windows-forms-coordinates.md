---
title: "Coordonnées Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a>Coordonnées Windows Forms
Le système de coordonnées pour un Windows Form est basé sur les coordonnées de périphérique, et l’unité de mesure lors du dessin dans les Windows Forms de base est l’unité de périphérique (en général, le pixel). Points à l’écran sont décrits par des paires de coordonnées x et y, avec les coordonnées x qui augmentent vers la droite et les coordonnées y augmentant de haut en bas. L’emplacement de l’origine, par rapport à l’écran, varient selon que vous spécifiez les coordonnées d’écran ou un client.  
  
## <a name="screen-coordinates"></a>Coordonnées d’écran  
 Une application Windows Forms spécifie la position d’une fenêtre à l’écran en coordonnées d’écran. Pour les coordonnées d’écran, l’origine sont l’angle supérieur gauche de l’écran. La position complète d’une fenêtre est souvent décrite par un <xref:System.Drawing.Rectangle> structure qui contient les coordonnées d’écran de deux points qui définissent les angles supérieur gauche et à droite de la fenêtre.  
  
## <a name="client-coordinates"></a>Coordonnées clientes  
 Une application Windows Forms spécifie la position des points dans un formulaire ou un contrôle à l’aide de coordonnées clientes. L’origine pour les coordonnées clientes est l’angle supérieur gauche de la zone cliente du contrôle ou du formulaire. Les coordonnées clientes garantissent qu’une application peut utiliser des valeurs de coordonnée cohérentes en dessinant dans un formulaire ou un contrôle, indépendamment de la position du formulaire ou contrôle sur l’écran.  
  
 Les dimensions de la zone cliente sont également décrites par un <xref:System.Drawing.Rectangle> structure qui contient les coordonnées clientes pour la zone. Dans tous les cas, les coordonnées du coin supérieur gauche du rectangle sont incluses dans la zone cliente, alors que la coordonnée inférieur droit est exclue. Opérations graphiques n’incluent pas les bords droit et inférieurs d’une zone cliente. Par exemple le <xref:System.Drawing.Graphics.FillRectangle%2A> méthode arrive à saturation et le bord droit et inférieur du rectangle spécifié, mais n’inclura pas ces bords.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mappage d’un Type de coordonnées à un autre  
 Parfois, vous devrez peut-être mapper des coordonnées d’écran en coordonnées clientes. Vous pouvez le faire facilement à l’aide de la <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> méthodes disponibles dans la <xref:System.Windows.Forms.Control> classe. Par exemple, le <xref:System.Windows.Forms.Control.MousePosition%2A> propriété du <xref:System.Windows.Forms.Control> est signalée en coordonnées d’écran, mais vous pouvez convertir celles-ci en coordonnées clientes.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
