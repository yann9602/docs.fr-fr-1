---
title: "Vue d&#39;ensemble des graphismes | Microsoft Docs"
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
  - "graphiques, à propos des graphiques"
  - "graphiques, utiliser l'interface managée"
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Vue d&#39;ensemble des graphismes
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est une interface de programmation d'applications \(API\) qui forme le sous\-système du système d'exploitation Microsoft Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est responsable de l'affichage des informations sur les écrans et les imprimantes.  Comme son nom le suggère, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est le successeur de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], l'interface GDI \(Graphics Device Interface\) fournie avec les versions antérieures de Windows.  
  
## Interface de classes managées  
 L'API [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est exposée via un ensemble de classes déployées comme du code managé.  Cet ensemble de classes est appelé *interface de classes managées* dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  Les espaces de noms suivants composent l'interface de classes managées :  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 Avec une interface GDI telle que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez afficher des informations sur un écran ou une imprimante sans avoir à vous soucier des détails d'un périphérique d'affichage donné.  Le programmeur effectue des appels aux méthodes fournies par les classes [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Ces méthodes effectuent ensuite les appels appropriés aux pilotes de périphériques spécifiques.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] isole l'application du matériel graphique. C'est cette isolation qui permet à un programmeur de créer des applications indépendantes du périphérique.  
  
## Voir aussi  
 [Vue d'ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)