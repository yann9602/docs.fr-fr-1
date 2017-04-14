---
title: "Comment&#160;:d&#233;terminer la version install&#233;e de WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "version, rechercher"
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# Comment&#160;:d&#233;terminer la version install&#233;e de WPF
Vous pouvez trouver le numéro de la version actuellement installée de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans le **Registre**.  
  
 Pour rechercher le numéro de version :  
  
1.  Dans le menu **Démarrer**, cliquez sur **Exécuter**.  
  
2.  Dans **Ouvrir**, tapez **regedit.exe**.  
  
3.  Ouvrez la clé suivante :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 Le numéro de version de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est stocké dans la valeur **Version**.