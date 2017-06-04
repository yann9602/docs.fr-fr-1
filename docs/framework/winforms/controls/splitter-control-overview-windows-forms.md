---
title: "Vue d&#39;ensemble du contr&#244;le Splitter (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Splitter"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Splitter (contrôle Windows Forms), à propos du contrôle Splitter"
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble du contr&#244;le Splitter (Windows Forms)
> [!IMPORTANT]
>  Bien que <xref:System.Windows.Forms.SplitContainer> remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.Splitter> des versions antérieures, <xref:System.Windows.Forms.Splitter> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Les contrôles <xref:System.Windows.Forms.Splitter> Windows Forms servent à redimensionner des contrôles ancrés au moment de l'exécution.  Le contrôle <xref:System.Windows.Forms.Splitter> est souvent utilisé dans les formulaires dont les contrôles doivent présenter des données de longueurs variables, comme l'Explorateur Windows, dont les volets de données contiennent des informations de longueur différente à différents moments.  
  
## Utilisation du contrôle Splitter  
 Lorsque l'utilisateur place le pointeur de la souris sur le bord non ancré d'un contrôle qui peut être redimensionné par un contrôle Splitter, le pointeur change d'apparence afin d'indiquer que le contrôle peut être redimensionné.  Le contrôle Splitter permet à l'utilisateur de redimensionner le contrôle ancré qui le précède directement.  Par conséquent, pour permettre à un utilisateur de redimensionner un contrôle ancré au moment de l'exécution, ancrez le contrôle à redimensionner au bord d'un conteneur, puis ancrez un contrôle Splitter sur le même côté de ce conteneur.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)