---
title: Graphiques et dessins dans les Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ae9810b10a7357f7f8d00783335335a391a5211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Graphiques et dessins dans les Windows Forms
Le Common Language Runtime utilise une implémentation avancée de l'interface GDI Windows ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) appelée [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez créer des graphismes, dessiner du texte et manipuler des images graphiques comme des objets. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est conçu pour offrir à la fois de hautes performances et une facilité d'utilisation. Vous pouvez utiliser [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour restituer des images graphiques sur des Windows Forms et des contrôles. Bien que vous ne puissiez pas utiliser [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directement sur des Web Forms, vous pouvez afficher des images graphiques via le contrôle serveur web Image.  
  
 Dans cette section, vous trouverez des rubriques qui présentent les notions de base de la programmation [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Bien qu'il ne s'agisse pas d'une référence exhaustive, cette section comprend des informations sur les objets <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, et <xref:System.Drawing.Color> et explique comment effectuer des tâches telles que dessiner des formes et du texte ou afficher des images. Pour plus d’informations, consultez [référence GDI +](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).  
  
 Si vous voulez vous lancer et commencer immédiatement, consultez [Bien démarrer avec la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Elle comporte des rubriques sur l’utilisation de code pour dessiner des lignes, des formes, du texte et d’autres éléments sur les Windows Forms.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble des graphiques](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Fournit une introduction aux classes managées graphiques.  
  
 [À propos du code managé GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Fournit des informations sur les classes managées [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Montre comment effectuer diverses tâches à l'aide des classes managées [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
## <a name="reference"></a>Référence  
 <xref:System.Drawing>  
 Fournit l'accès aux fonctionnalités graphiques de base [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 <xref:System.Drawing.Drawing2D>  
 Fournit des fonctionnalités graphiques vectorielles et à deux dimensions avancées.  
  
 <xref:System.Drawing.Imaging>  
 Fournit des fonctionnalités d'imagerie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] avancées.  
  
 <xref:System.Drawing.Text>  
 Fournit des fonctionnalités typographiques [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] avancées. Les classes dans cet espace de noms peuvent être utilisées pour créer et utiliser des collections de polices.  
  
 <xref:System.Drawing.Printing>  
 Fournit des fonctionnalités d'impression.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Dessin et rendu personnalisés des contrôles](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Explique comment fournir du code pour des contrôles de dessin.
