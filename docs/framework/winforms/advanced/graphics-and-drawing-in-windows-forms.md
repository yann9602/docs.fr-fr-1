---
title: "Graphiques et dessins dans les Windows Forms | Microsoft Docs"
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
  - "dessiner (Windows Forms)"
  - "GDI+, utiliser dans le code managé"
  - "graphiques (Windows Forms)"
  - "graphiques, utiliser dans les Windows Forms"
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Graphiques et dessins dans les Windows Forms
Le Common Language Runtime utilise une implémentation avancée de l'interface GDI Windows \([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]\) appelée [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  Avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez créer des graphismes, dessiner du texte et manipuler des images graphiques comme des objets.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est conçu pour offrir à la fois de hautes performances et une facilité d'utilisation.  Vous pouvez utiliser [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour restituer des images graphiques sur des Windows Forms et des contrôles.  Bien que vous ne puissiez pas utiliser [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directement sur des Web Forms, vous pouvez afficher des images graphiques via le contrôle serveur web Image.  
  
 Dans cette section, vous trouverez des rubriques qui présentent les notions de base de la programmation [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  Bien qu'il ne s'agisse pas d'une référence exhaustive, cette section comprend des informations sur les objets <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, et <xref:System.Drawing.Color> et explique comment effectuer des tâches telles que dessiner des formes et du texte ou afficher des images.  Pour plus d'informations, consultez la rubrique « Référence GDI\+ » dans MSDN Library à l'adresse http:\/\/msdn.microsoft.com\/library.  
  
## Dans cette section  
 [Vue d'ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Fournit une introduction aux classes managées graphiques.  
  
 [À propos du code managé GDI\+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Fournit des informations sur les classes managées [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Montre comment effectuer diverses tâches à l'aide des classes managées [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
## Référence  
 <xref:System.Drawing>  
 Fournit l'accès aux fonctionnalités graphiques de base [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 <xref:System.Drawing.Drawing2D>  
 Fournit des fonctionnalités graphiques vectorielles et à deux dimensions avancées.  
  
 <xref:System.Drawing.Imaging>  
 Fournit des fonctionnalités d'imagerie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] avancées.  
  
 <xref:System.Drawing.Text>  
 Fournit des fonctionnalités typographiques [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] avancées.  Les classes dans cet espace de noms peuvent être utilisées pour créer et utiliser des collections de polices.  
  
 <xref:System.Drawing.Printing>  
 Fournit des fonctionnalités d'impression.  
  
## Rubriques connexes  
 [Peinture et rendu personnalisés des contrôles](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Explique comment fournir du code pour des contrôles de dessin.