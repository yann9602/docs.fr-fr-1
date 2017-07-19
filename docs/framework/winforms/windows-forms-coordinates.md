---
title: "Coordonn&#233;es Windows&#160;Forms | Microsoft Docs"
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
  - "coordonnées du client"
  - "coordonnées, Windows Forms"
  - "coordonnées de l'écran"
  - "coordonnées des Windows Forms"
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Coordonn&#233;es Windows&#160;Forms
Le système de coordonnées pour un Windows Form est basé sur les coordonnées de périphérique, et l'unité de mesure de base lorsque vous dessinez dans Windows Forms est l'unité de périphérique \(en général, le pixel\).  Les points sur l'écran sont décrits comme des paires de coordonnées x et y, avec les coordonnées x qui augmentent vers la droite et les coordonnées y qui augmentent de bas en haut.  L'emplacement de l'origine, relatif à l'écran, variera selon que vous spécifiez des coordonnées d'écran ou des coordonnées clientes.  
  
## Coordonnées d'écran  
 Une application Windows Forms spécifie la position d'une fenêtre sur l'écran en coordonnées d'écran.  Pour les coordonnées d'écran, l'origine est l'angle supérieur gauche de l'écran.  La position complète d'une fenêtre est souvent décrite par une structure <xref:System.Drawing.Rectangle> qui contient les coordonnées d'écran de deux points qui définissent les coins supérieur gauche et inférieur droit de la fenêtre.  
  
## Coordonnées clientes  
 Une application Windows Forms spécifie la position de points dans un formulaire ou contrôle à l'aide de coordonnées clientes.  L'origine pour les coordonnées clientes est l'angle supérieur gauche de la zone cliente du contrôle ou formulaire.  Les coordonnées clientes garantissent qu'une application peut utiliser des valeurs de coordonnée cohérentes en dessinant dans un formulaire ou contrôle, indépendamment de la position du formulaire ou contrôle sur l'écran.  
  
 Les dimensions de la zone cliente sont également décrites par une structure <xref:System.Drawing.Rectangle> qui contient des coordonnées clientes pour la zone.  Dans tous les cas, la coordonnée supérieure gauche du rectangle est incluse dans la zone cliente, alors que la coordonnée de l'angle inférieur droit est exclue.  Les opérations graphiques n'incluent pas les bords droit et inférieur d'une zone cliente.  Par exemple, la méthode <xref:System.Drawing.Graphics.FillRectangle%2A> remplira jusqu'au bord droit et inférieur du rectangle spécifié, mais n'inclura pas ces bords.  
  
## Mappage d'un type de coordonnée à un autre  
 Parfois, vous pouvez devoir mapper des coordonnées d'écran aux coordonnées clientes.  Vous pouvez le faire facilement en utilisant les méthodes <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> disponibles dans la classe <xref:System.Windows.Forms.Control>.  Par exemple, la propriété <xref:System.Windows.Forms.Control.MousePosition%2A> de <xref:System.Windows.Forms.Control> est rapportée dans les coordonnées d'écran, mais vous pouvez convertir celles\-ci en coordonnées clientes.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.PointToClient%2A>   
 <xref:System.Windows.Forms.Control.PointToScreen%2A>