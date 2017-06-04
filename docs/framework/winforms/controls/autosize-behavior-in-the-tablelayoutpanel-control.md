---
title: "Comportement du redimensionnement automatique dans le contr&#244;le TableLayoutPanel | Microsoft Docs"
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
  - "dimensionnement automatique"
  - "AutoSize (propriété), TableLayoutPanel (contrôle)"
  - "AutoSizeMode (propriété)"
  - "contrôles (Windows Forms), dimensionner"
  - "disposition (Windows Forms), AutoSize"
  - "localiser des formulaires"
  - "dimensionner, automatique"
  - "TableLayoutPanel (contrôle Windows Forms), AutoSize (comportement)"
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comportement du redimensionnement automatique dans le contr&#244;le TableLayoutPanel
## Comportements de redimensionnement automatique distincts  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> prend en charge le comportement de redimensionnement automatique des façons suivantes :  
  
-   via la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> ;  
  
-   par le biais de la propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> sur les styles de ligne et de colonne du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
### La propriété AutoSize avec les styles de ligne et de colonne  
 Le tableau suivant décrit l'interaction entre la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> et les styles de ligne et de colonne du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
|Paramètre de redimensionnement automatique|Interaction de style|  
|------------------------------------------------|--------------------------|  
|`false`|Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> opère de gauche à droite, et alloue de l'espace pour la colonne ou la ligne dans l'ordre suivant.<br /><br /> 1.  Si la propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> a la valeur <xref:System.Windows.Forms.SizeType>, le nombre de pixels spécifié par <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> est alloué.<br />2.  Si la propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> a la valeur <xref:System.Windows.Forms.SizeType>, le nombre de pixels retourné par la méthode <xref:System.Windows.Forms.Control.GetPreferredSize%2A> du contrôle enfant est alloué.<br />3.  Une fois l'espace alloué pour toutes les colonnes et les lignes <xref:System.Windows.Forms.SizeType> et <xref:System.Windows.Forms.SizeType>, toutes les colonnes ou lignes pour lesquelles <xref:System.Windows.Forms.SizeType> est affecté à <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> sont utilisées pour allouer l'espace libre restant proportionnellement|  
|`true`|Semblable à l'interaction précédente, sauf que les colonnes ou lignes <xref:System.Windows.Forms.SizeType> acquièrent un aspect de dimensionnement automatique.<br /><br /> Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> développe la colonne ou ligne pour créer l'espace libre adéquat, afin qu'aucune colonne ou ligne avec les styles <xref:System.Windows.Forms.SizeType> ne découpe son contenu.  Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> alloue proportionnellement le nouvel espace en fonction de la propriété <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A>.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [Vue d'ensemble du contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)