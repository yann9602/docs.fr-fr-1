---
title: "Utilisation de doubles tampons d&#39;enregistrements | Microsoft Docs"
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
  - "mettre en mémoire tampon, doubles tampons"
  - "doubles tampons"
  - "scintillement, réduire dans les Windows Forms"
  - "graphiques, doubles tampons"
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Utilisation de doubles tampons d&#39;enregistrements
Vous pouvez utiliser des graphiques à double tampon pour réduire le scintillement dans vos applications où sont effectuées des opérations de peinture complexes.  La prise en charge du mécanisme de double tampon est intégrée au .NET Framework, mais vous pouvez gérer et restituer les graphiques manuellement.  
  
## Dans cette section  
 [Graphiques mis deux fois en mémoire tampon](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 Présente le concept de double tampon et décrit brièvement la prise en charge du .NET Framework.  
  
 [Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Décrit comment utiliser la prise en charge du mécanisme de double tampon par défaut dans le .NET Framework.  
  
 [Comment : gérer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 Montre comment gérer le mécanisme de double tampon dans les applications.  
  
 [Comment : restituer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 Décrit comment restituer les graphiques à double tampon.  
  
## Référence  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 Méthode de contrôle qui active le mécanisme de double tampon.  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 Fournit des méthodes pour créer des mémoires tampon de graphiques.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Fournit l'accès au contexte graphique mis en mémoire tampon pour un domaine d'application.