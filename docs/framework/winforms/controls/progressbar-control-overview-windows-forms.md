---
title: "Vue d&#39;ensemble du contr&#244;le ProgressBar (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ProgressBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Progress (contrôles), à propos des contrôles Progress"
  - "ProgressBar (contrôle Windows Forms), à propos du contrôle ProgressBar"
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble du contr&#244;le ProgressBar (Windows Forms)
> [!IMPORTANT]
>  Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le contrôle <xref:System.Windows.Forms.ProgressBar> Windows Forms indique l'état d'avancement d'un processus par l'affichage d'un nombre approprié de rectangles disposés dans une barre horizontale.  Lorsque le processus est terminé, la barre est entièrement remplie.  Les barres de progression sont couramment utilisées pour indiquer à l'utilisateur le temps qu'il doit encore attendre avant qu'un processus ne se termine, par exemple dans le cas du chargement d'un fichier volumineux.  
  
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ProgressBar> peut uniquement être orienté horizontalement sur le formulaire.  
  
## Propriétés et méthodes principales  
 Les principales propriétés du contrôle <xref:System.Windows.Forms.ProgressBar> sont <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A>.  Les propriétés <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> définissent les valeurs maximale et minimale que la barre de progression peut afficher.  La propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> représente la progression de l'opération.  Dans la mesure où la barre affichée dans le contrôle est constituée de blocs, la valeur affichée par le contrôle <xref:System.Windows.Forms.ProgressBar> n'est qu'une approximation de la valeur actuelle de la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  En fonction de la taille du contrôle <xref:System.Windows.Forms.ProgressBar>, la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> détermine à quel moment afficher le bloc suivant.  
  
 Le moyen le plus courant de mettre à jour la valeur de progression actuelle consiste à écrire du code pour définir la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  Dans l'exemple du chargement d'un gros fichier, la valeur maximale définie peut correspondre à la taille en kilo\-octets du fichier.  Par exemple, si la propriété <xref:System.Windows.Forms.ProgressBar.Maximum%2A> a la valeur 100, la propriété <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a la valeur 10 et la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> a la valeur 50, 5 rectangles seront affichés.  C'est la moitié du nombre qui peut être affiché.  
  
 Cependant, il existe d'autres moyens de modifier la valeur affichée par le contrôle <xref:System.Windows.Forms.ProgressBar>, outre la définition directe de la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  La propriété <xref:System.Windows.Forms.ProgressBar.Step%2A> peut être utilisée pour spécifier une valeur d'incrémentation de la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  Ensuite, l'appel à la méthode <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> incrémente la valeur.  Pour varier la valeur de l'incrément, vous pouvez utiliser la méthode <xref:System.Windows.Forms.ProgressBar.Increment%2A> et préciser une valeur d'incrémentation de la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  
  
 <xref:System.Windows.Forms.StatusBar> est un autre contrôle graphique qui informe l'utilisateur sur l'état d'avancement de l'action en cours.  
  
> [!IMPORTANT]
>  Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> et y ajoutent des fonctionnalités ; toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ProgressBar>   
 [ProgressBar, contrôle](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)