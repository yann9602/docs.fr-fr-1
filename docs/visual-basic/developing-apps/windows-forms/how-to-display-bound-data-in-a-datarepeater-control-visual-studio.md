---
title: "How to: Display Bound Data in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "DataRepeater, data-binding"
  - "DataRepeater, displaying bound controls"
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Display Bound Data in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est le plus souvent utilisé pour afficher des données liées à partir d'une base de données ou d'une autre source de données.  
  
 En plus de contrôles dépendants, vous pouvez ajouter d'autres contrôles, tels qu'une étiquette statique ou une image répétée sur chacun des éléments dans le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Pour plus d'informations, consultez [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Vous pouvez également créer une liaison avec une source de données au moment de l'exécution en définissant la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> à la valeur `True` et en assignant une source de données à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>.  Dans ce cas, vous devrez gérer toute l'interaction avec la source de données.  Pour plus d'informations, consultez [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Pour créer un DataRepeater lié aux données  
  
1.  Faites glisser un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> depuis l'onglet **Visual Basic PowerPacks** de la **Boîte à outils** vers un formulaire ou un contrôle conteneur.  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour changer la taille et la position du contrôle.  
  
     Notez que le contrôle possède deux régions rectangulaires.  La région supérieure correspond au *modèle d'élément* ; les contrôles ajoutés au modèle seront répétés dans chacun des éléments du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> au moment de l'exécution.  La région inférieure est la *fenêtre d'affichage*, dans laquelle les éléments seront affichés.  
  
     Vous pouvez également redimensionner et déplacer le contrôle ou le modèle d'élément en modifiant les propriétés **Size** et **Position** dans la fenêtre Propriétés.  
  
3.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** est vide, ajoutez\-y une source de données.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](/visual-studio/data-tools/add-new-data-sources).  
  
4.  Dans la fenêtre **Sources de données**, sélectionnez le nœud de niveau supérieur de la table qui contient les données que vous souhaitez lier.  
  
5.  Configurez le type de déplacement de la table sur `Details` en cliquant sur `Details` dans la liste déroulante du nœud table.  
  
6.  Sélectionnez le nœud table et faites\-le glisser sur la région de modèle d'élément du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
     Vous pouvez spécifier les types de contrôle à afficher pour chaque champ.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](/visual-studio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)