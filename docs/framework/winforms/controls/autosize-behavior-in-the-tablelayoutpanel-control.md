---
title: "Comportement du redimensionnement automatique dans le contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06bd0686b31b52ccb8580a545910339d2e2cd5bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>Comportement du redimensionnement automatique dans le contrôle TableLayoutPanel
## <a name="distinct-autosize-behaviors"></a>Comportements de redimensionnement automatique distincts  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle prend en charge le comportement de dimensionnement automatique des manières suivantes :  
  
-   Via le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété ;  
  
-   Via le <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriété sur le <xref:System.Windows.Forms.TableLayoutPanel> les styles de ligne et de colonne du contrôle.  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>La propriété AutoSize avec les Styles de colonne et de ligne  
 Le tableau suivant décrit l’interaction entre le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété et la <xref:System.Windows.Forms.TableLayoutPanel> les styles de ligne et de colonne du contrôle.  
  
|Paramètre de redimensionnement automatique|Interaction de style|  
|----------------------|-----------------------|  
|`false`|Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle opère de gauche à droite et alloue de l’espace pour la colonne ou la ligne ou dans l’ordre suivant.<br /><br /> 1.  Si le <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> est définie sur <xref:System.Windows.Forms.SizeType.Absolute>, le nombre de pixels spécifié par <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> est allouée.<br />2.  Si le <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> est définie sur <xref:System.Windows.Forms.SizeType.AutoSize>, le nombre de pixels retourné par le contrôle d’enfant <xref:System.Windows.Forms.Control.GetPreferredSize%2A> (méthode) est allouée.<br />3.  Après l’espace pour toutes les <xref:System.Windows.Forms.SizeType.Absolute> et <xref:System.Windows.Forms.SizeType.AutoSize> les colonnes ou lignes est alloué, des colonnes ou des lignes avec <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> la valeur <xref:System.Windows.Forms.SizeType.Percent> sont utilisées pour allouer l’espace libre restant proportionnellement|  
|`true`|Semblable à l’interaction précédente, avec l’exception qui <xref:System.Windows.Forms.SizeType.Percent> les colonnes ou lignes acquièrent un aspect de dimensionnement automatique.<br /><br /> Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle développe la colonne ou ligne pour créer un espace adéquat, afin qu’aucune colonne ou ligne avec <xref:System.Windows.Forms.SizeType.Percent> style découpe son contenu. Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle alloue le nouvel espace proportionnellement en fonction de la <xref:System.Windows.Forms.ColumnStyle.Width%2A> ou <xref:System.Windows.Forms.RowStyle.Height%2A> propriété.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Vue d’ensemble du contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
