---
title: "How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, master/detail tables"
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez afficher des données liées à l'aide de deux contrôles <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou plus créer un formulaire maître\/détail.  Par exemple, vous pouvez décider d'afficher une liste de clients dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> et, lorsque l'utilisateur sélectionne un client, d'afficher une liste des ordres de ce client dans un deuxième <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Vous pouvez afficher les données liées en faisant glisser des éléments de détail qui partagent le même nœud de la table principale depuis la fenêtre **Sources de données** sur un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Par exemple, si vous possédez une source de données contenant une table Customers et une table Orders connexe, les deux tables s'affichent en tant que nœuds de niveau supérieur dans l'arborescence dans la fenêtre **Sources de données**.  Développez le nœud Clients de manière à voir les colonnes.  Notez que la dernière colonne de la liste est un nœud extensible qui représente la table Orders.  Ce nœud représente les commandes connexes d'un client.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour afficher des données liées dans des contrôles DataRepeater  
  
1.  Faites glisser deux contrôles <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> depuis l'onglet **Visual Basic PowerPacks** de la **Boîte à outils** vers un formulaire ou un contrôle conteneur.  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour redimensionner les contrôles et les positionner côte à côte.  
  
3.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** est vide, ajoutez\-y une source de données.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](/visual-studio/data-tools/add-new-data-sources).  
  
4.  Dans la fenêtre **Sources de données**, sélectionnez le nœud de niveau supérieur de la table principale.  
  
5.  Configurez le type de déplacement de la table principale sur Détails en cliquant sur **Détails** dans la liste déroulante du nœud table.  
  
6.  Faites glisser le nœud de la table principale sur la région de modèle d'élément du premier contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
7.  Développez le nœud de la table principale et sélectionnez le nœud secondaire de la table connexe.  
  
8.  Configurez le type de déplacement de la table secondaire sur Détails en cliquant sur **Détails** dans la liste déroulante du nœud table.  
  
9. Sélectionnez ce nœud table et faites\-le glisser sur la région de modèle d'élément du deuxième contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)