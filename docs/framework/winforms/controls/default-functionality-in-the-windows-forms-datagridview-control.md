---
title: "Fonctionnalit&#233;s par d&#233;faut du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "grilles de données, fonctionnalité par défaut du contrôle DataGridView"
  - "DataGridView (contrôle Windows Forms), fonctionnalité par défaut"
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Fonctionnalit&#233;s par d&#233;faut du contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms fournit aux utilisateurs un nombre significatif de fonctionnalités par défaut.  
  
## Fonctionnalités par défaut  
 Par défaut, un contrôle <xref:System.Windows.Forms.DataGridView> :  
  
-   affiche automatiquement des en\-têtes de colonne et de ligne qui restent visibles lors du défilement vertical du tableau ;  
  
-   possède un en\-tête de ligne qui contient un indicateur de sélection pour la ligne actuelle.  
  
-   possède un rectangle de sélection dans la première cellule ;  
  
-   possède des colonnes qui peuvent être automatiquement redimensionnées en double\-cliquant sur les séparateurs de colonne.  
  
-   prend automatiquement en charge des styles visuels sur Windows XP et la famille Windows Server 2003 lorsque la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> est appelée à partir de la méthode `Main` de l'application.  
  
 De plus, le contenu d'un contrôle <xref:System.Windows.Forms.DataGridView> peut être modifié par défaut :  
  
-   Si l'utilisateur double\-clique ou appuie sur la touche F2 dans une cellule, le contrôle passe automatiquement la cellule en mode Édition et met à jour son contenu en tant que types utilisateur.  
  
-   Si l'utilisateur fait défiler la grille jusqu'en bas, il verra une ligne permettant d'ajouter de nouveaux enregistrements.  Lorsque l'utilisateur clique sur cette ligne, une nouvelle ligne est ajoutée au contrôle <xref:System.Windows.Forms.DataGridView>, avec les valeurs par défaut.  Lorsque l'utilisateur appuie sur la touche Échap, cette nouvelle ligne disparaît.  
  
-   Si l'utilisateur clique sur un en\-tête de ligne, la ligne entière est sélectionnée.  
  
 Lorsque vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une source de données en définissant sa propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>, le contrôle :  
  
-   utilise automatiquement les noms des colonnes de la source de données comme texte d'en\-tête de colonne ;  
  
-   Est rempli avec le contenu de la source de données.  Des colonnes <xref:System.Windows.Forms.DataGridView> sont créées automatiquement pour chaque colonne de la source de données.  
  
-   crée une ligne pour chaque ligne visible du tableau ;  
  
-   trie automatiquement les lignes en fonction des données sous\-jacentes lorsque l'utilisateur clique sur un en\-tête de colonne.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)