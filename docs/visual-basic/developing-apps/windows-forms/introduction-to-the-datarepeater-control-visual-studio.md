---
title: "Introduction to the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "repeating data"
  - "DataRepeater, overview"
  - "DataRepeater"
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Introduction to the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> de Visual Basic Power Packs est un conteneur à défilement destiné aux contrôles qui affichent des données répétées, telles que des lignes dans une table de base de données.  Il peut être utilisé en guise d'alternative au contrôle <xref:System.Windows.Forms.DataGridView> lorsque vous avez besoin d'un plus grand contrôle sur la disposition des données.  Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "répète" un groupe de contrôles connexes en créant plusieurs instances dans une vue de défilement.  Vous pouvez ainsi visualiser simultanément plusieurs enregistrements.  
  
## Vue d'ensemble  
 Au moment du design, le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> comprend deux sections.  La section externe correspond à la *fenêtre d'affichage*, dans laquelle les données de défilement seront affichées au moment de l'exécution.  La section interne \(supérieur\), appelée *modèle d'élément*, est l'endroit où vous positionnez des contrôles qui seront répétés au moment de l'exécution \(en général, un contrôle pour chaque champ de la source de données\).  Les propriétés et les contrôles du modèle d'élément sont encapsulés dans la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>.  
  
 Au moment de l'exécution, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> est copié vers un objet <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> virtuel qui est utilisé pour afficher les données lorsque chaque enregistrement fait l'objet d'un défilement dans l'affichage.  Vous pouvez personnaliser l'affichage d'enregistrements individuels dans l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> en mettant par exemple un champ en surbrillance en fonction de la valeur qu'il contient.  Pour plus d'informations, consultez [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est le plus souvent utilisé pour afficher des données à partir d'une table de base de données ou d'une autre source de données liée.  Outre les objets de données [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)], le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> peut créer une liaison avec toute classe qui implémente l'interface <xref:System.Collections.IList> \(y compris les tableaux\), <xref:System.ComponentModel.IListSource>, <xref:System.ComponentModel.IBindingList> ou <xref:System.ComponentModel.IBindingListView>.  
  
### Liaison de données  
 En général, la liaison des données est effectuée en faisant glisser des champs de la fenêtre **Sources de données** sur le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.  Pour plus d'informations, consultez [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Lorsque vous travaillez avec d'importantes quantités de données, vous pouvez affecter la valeur `True` à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> pour afficher un sous\-ensemble des données disponibles.  Le mode virtuel requiert l'implémentation d'un cache de données à partir duquel le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est rempli. Vous devez contrôler toutes les interactions avec le cache de données au moment de l'exécution.  Pour plus d'informations, consultez [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Vous pouvez également afficher des contrôles indépendants sur un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Par exemple, vous pouvez afficher une image répétée sur chaque élément.  Pour plus d'informations, consultez [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### Événements  
 Les événements les plus importants pour le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sont l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>, qui est déclenché lorsque de nouveaux éléments font l'objet d'un défilement dans l'affichage, et l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>, qui est déclenché lorsqu'un élément est sélectionné.  Vous pouvez utiliser l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> pour changer l'apparence de l'élément.  Vous pouvez par exemple mettre en surbrillance les valeurs négatives.  Utilisez l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> pour accéder aux valeurs des contrôles lorsqu'un élément est sélectionné.  
  
 Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> expose tous les événements de contrôle standard dans l'Éditeur de code.  Certains événements ne doivent cependant pas être utilisés.  Les événements de clavier et de souris tels que `KeyDown`, `Click` et `MouseDown` ne sont pas déclenchés au moment de l'exécution car le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> n'a jamais le focus.  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> n'expose pas d'événements au moment du design dans la mesure où il est seulement créé au moment de l'exécution.  Si vous souhaitez gérer des événements de clavier et de souris, vous pouvez ajouter un contrôle <xref:System.Windows.Forms.Panel> au <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> au moment du design, puis gérer les événements pour le <xref:System.Windows.Forms.Panel>.  Pour plus d'informations, consultez [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### Personnalisations  
 Il existe de nombreuses façons de personnaliser l'apparence et du comportement du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, tant au moment de l'exécution que du design.  Des propriétés peuvent être configurées pour modifier les couleurs, masquer ou modifier les en\-têtes d'élément, passer de l'orientation verticale à l'horizontale, etc.  Pour plus d'informations, consultez [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) et [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Notez que certaines propriétés s'appliquent au contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> lui\-même tandis que d'autres s'appliquent uniquement au <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>.  Prenez soin de sélectionner la section correcte du contrôle avant de définir des propriétés.  Pour plus d'informations, consultez [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 D'autres personnalisations permettent de contrôler la capacité d'ajout ou de suppression d'enregistrements, d'ajouter des fonctions de recherche et d'afficher des données connexes dans un format maître\/détail.  Pour plus d'informations, consultez [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) et [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## Voir aussi  
 [DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [Procédure pas à pas : affichage de données dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)