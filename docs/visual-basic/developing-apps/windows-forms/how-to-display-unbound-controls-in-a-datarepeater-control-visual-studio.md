---
title: "Comment : afficher les contrôles indépendants dans un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Comment : afficher les contrôles indépendants dans un contrôle DataRepeater (Visual Studio)
En plus de contrôles dépendants, vous voudrez ajouter d’autres contrôles à un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, tel qu’une étiquette statique ou une image qui est répétée sur chaque élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
> [!NOTE]
>  Vous devez également disposer au moins un contrôle lié sur le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou rien ne s’affichera au moment de l’exécution.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Pour ajouter des contrôles indépendants à un contrôle DataRepeater  
  
1.  Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour dimensionner et positionner le contrôle.  
  
     Vous pouvez également redimensionner et positionner le contrôle en modifiant le **taille** et **Position** propriétés dans la fenêtre Propriétés.  
  
3.  Ajoutez au moins un contrôle lié aux données à le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Pour plus d’informations, consultez [Comment : afficher les données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Faites glisser un contrôle de la **boîte à outils** sur la région de modèle d’élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
     Notez que le contrôle possède deux régions rectangulaires. La région interne est la *modèle d’élément*; les contrôles ajoutés au modèle seront répétés dans chaque élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle au moment de l’exécution. La région externe est la *la fenêtre d’affichage*, où les éléments seront affiche ; les contrôles qui sont ajoutés à cette région ne s’affichera pas en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Guide pratique : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
