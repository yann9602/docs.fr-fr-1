---
title: "Utilisation de conteneurs graphiques | Microsoft Docs"
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
  - "exemples (Windows Forms), conteneurs graphiques"
  - "conteneurs graphiques"
  - "graphiques, utiliser les conteneurs"
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Utilisation de conteneurs graphiques
Un objet <xref:System.Drawing.Graphics> fournit des méthodes telles que <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A> et <xref:System.Drawing.Graphics.DrawString%2A> pour afficher des images vectorielles, des images raster et du texte.  Un objet <xref:System.Drawing.Graphics> possède également plusieurs propriétés qui influencent la qualité et l'orientation des éléments dessinés.  Ainsi, la propriété en mode lissage détermine si l'anticrénelage s'applique aux traits et aux courbes, tandis que la propriété de transformation universelle influence la position et la rotation des éléments dessinés.  
  
 Un objet <xref:System.Drawing.Graphics> est associé à un périphérique donné.  Lorsque vous utilisez un objet <xref:System.Drawing.Graphics> pour dessiner dans une fenêtre, l'objet <xref:System.Drawing.Graphics> est également associé à cette fenêtre particulière.  
  
 Un objet <xref:System.Drawing.Graphics> peut être représenté comme un conteneur car il contient un ensemble de propriétés ayant une incidence sur le dessin et est lié à des informations spécifiques aux périphériques.  Vous pouvez créer un conteneur secondaire dans un objet <xref:System.Drawing.Graphics> existant en appelant la méthode <xref:System.Drawing.Graphics.BeginContainer%2A> de cet objet <xref:System.Drawing.Graphics>.  
  
## Dans cette section  
 [Gestion de l'état d'un objet graphique](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 Décrit la gestion des paramètres de qualité, la zone de découpage  et les transformations d'un objet <xref:System.Drawing.Graphics>.  
  
 [Utilisation de conteneurs graphiques imbriqués](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 Indique comment utiliser des conteneurs pour contrôler l'état de l'objet <xref:System.Drawing.Graphics>.