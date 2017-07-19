---
title: "Vue d&#39;ensemble du contr&#244;le SplitContainer (Windows Forms) | Microsoft Docs"
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
  - "SplitContainer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "SplitContainer (contrôle Windows Forms), à propos du contrôle SplitContainer"
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du contr&#244;le SplitContainer (Windows Forms)
Le contrôle <xref:System.Windows.Forms.SplitContainer> Windows Forms peut être considéré comme un composite ; il s'agit de deux panneaux séparés par une barre mobile.  Lorsque le pointeur de la souris est sur la barre, il change de forme pour montrer que la barre est mobile.  
  
> [!IMPORTANT]
>  Dans la **Boîte à outils**, le contrôle <xref:System.Windows.Forms.SplitContainer> remplace le contrôle <xref:System.Windows.Forms.Splitter> qui était utilisé dans la version antérieure de [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  Le contrôle <xref:System.Windows.Forms.SplitContainer> est préféré au contrôle <xref:System.Windows.Forms.Splitter>.  La classe <xref:System.Windows.Forms.Splitter> est toujours incluse dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour des raisons de compatibilité avec les applications existantes, mais il est fortement recommandé d'utiliser le contrôle <xref:System.Windows.Forms.SplitContainer> pour les nouveaux projets.  
  
 Avec le contrôle <xref:System.Windows.Forms.SplitContainer>, vous pouvez créer des interfaces utilisateur complexes ; une sélection dans un panneau détermine souvent les objets affichés dans l'autre panneau.  Cette disposition est très efficace pour l'affichage et l'exploration des informations.  Le fait d'avoir deux panneaux vous permet de regrouper des informations dans des zones et la barre, ou « séparateur », permet aux utilisateurs de redimensionner aisément les panneaux.  
  
 Plusieurs contrôles <xref:System.Windows.Forms.SplitContainer> peuvent également être imbriqués, avec le deuxième contrôle <xref:System.Windows.Forms.SplitContainer> orienté horizontalement, pour créer des panneaux inférieur et supérieur.  
  
 N'oubliez pas que le contrôle <xref:System.Windows.Forms.SplitContainer> est accessible par le clavier par défaut ; les utilisateurs peuvent appuyer sur les touches de direction pour déplacer le séparateur si la propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> a la valeur `false`.  
  
 La propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A> du contrôle <xref:System.Windows.Forms.SplitContainer> détermine la direction du séparateur et non du contrôle lui\-même.  Par conséquent, lorsque cette propriété a la valeur <xref:System.Windows.Forms.Orientation>, le séparateur s'exécute de haut en bas, en créant des panneaux gauche et droit.  
  
 En outre, n'oubliez pas que la valeur de la propriété <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> varie selon la valeur de la propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A>.  Pour plus d'informations, consultez la propriété <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>.  
  
 Vous pouvez également restreindre la taille et le déplacement du contrôle <xref:System.Windows.Forms.SplitContainer>.  La propriété <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> détermine le panneau qui conservera la même taille après le redimensionnement du contrôle <xref:System.Windows.Forms.SplitContainer>, et la propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> détermine si le séparateur est mobile par le clavier ou la souris.  
  
> [!NOTE]
>  Même si la propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> a la valeur `true`, le séparateur peut encore être déplacé par programme ; par exemple, en utilisant la propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>.  
  
 Enfin, chaque panneau du contrôle <xref:System.Windows.Forms.SplitContainer> a des propriétés permettant de déterminer sa taille individuelle.  
  
## Propriétés, méthodes et événements fréquemment utilisés  
  
|Nom|Description|  
|---------|-----------------|  
|Propriété <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Détermine le panneau qui conservera la même taille après le redimensionnement du contrôle <xref:System.Windows.Forms.SplitContainer>.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Détermine si le séparateur peut être déplacé avec le clavier ou la souris.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A>|Détermine si le séparateur est disposé verticalement ou horizontalement.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Détermine la distance en pixels entre le bord gauche ou supérieur et la barre de fractionnement mobile.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Détermine la distance minimale, en pixels, que l'utilisateur peut faire parcourir au séparateur.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>|Détermine l'épaisseur, en pixels, du séparateur.|  
|Événement <xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Se produit lorsque le séparateur se déplace.|  
|Événement <xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Se produit lorsque le séparateur s'est déplacé.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)   
 [SplitContainer Control Sample](http://msdn.microsoft.com/fr-fr/9015fad0-7108-4d85-a83a-a72d038c4f65)