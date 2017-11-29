---
title: Vue d'ensemble des graphismes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0a3286cbcaa0eebf59500582a749804b5e1b8ba
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="overview-of-graphics"></a>Vue d'ensemble des graphismes
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]est une interface de programmation d’applications (API) qui forme le sous-système du système d’exploitation Microsoft Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]est responsable de l’affichage des informations sur les écrans et les imprimantes. Comme son nom le suggère, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est le successeur de [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], l'interface GDI (Graphics Device Interface) fournie avec les versions antérieures de Windows.  
  
## <a name="managed-class-interface"></a>Interface de classes managées  
 Le [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API est exposée via un ensemble de classes déployées comme du code managé. Cet ensemble de classes est appelé le *interface de classes managées* à [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Les espaces de noms suivants composent l'interface de classes managées :  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 Avec une Interface graphique, tels que [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez afficher des informations sur un écran ou une imprimante sans avoir à se soucier des détails d’un périphérique d’affichage particulier. Le programmeur effectue des appels aux méthodes fournies par les classes [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Ces méthodes effectuent ensuite les appels appropriés aux pilotes de périphériques spécifiques. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] isole l'application du matériel graphique. C’est cette isolation qui permet à un programmeur de créer des applications indépendantes du périphérique.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
