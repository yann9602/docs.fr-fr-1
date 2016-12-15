---
title: "How to: Display Unbound Controls in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, adding unbound controls"
  - "DataRepeater"
  - "displaying unbound data"
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En plus des contrôles dépendants, vous pouvez ajouter d'autres contrôles à <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, tels qu'une étiquette statique ou une image répétée sur chacun des éléments dans le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
> [!NOTE]
>  Vous devez également avoir au moins un contrôle dépendant sur le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, sinon rien ne sera affiché au moment de l'exécution.  
  
### Pour ajouter des contrôles indépendants à un DataRepeater  
  
1.  Faites glisser un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> depuis l'onglet **Visual Basic PowerPacks** de la **Boîte à outils** vers un formulaire ou un contrôle conteneur.  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour changer la taille et la position du contrôle.  
  
     Vous pouvez également redimensionner et déplacer le contrôle en modifiant les propriétés **Size** et **Position** dans la fenêtre Propriétés.  
  
3.  Ajoutez au moins un contrôle lié aux données au contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Pour plus d'informations, consultez [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Faites glisser un contrôle depuis la **Boîte à outils** sur la région de modèle d'élément du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
     Notez que le contrôle possède deux régions rectangulaires.  La région intérieure correspond au *modèle d'élément* ; les contrôles ajoutés au modèle seront répétés dans chacun des éléments du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> au moment de l'exécution.  La région extérieure correspond à la *fenêtre d'affichage*, dans laquelle les éléments seront affichés ; les contrôles ajoutés à cette région ne s'affichent pas au moment de l'exécution.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)