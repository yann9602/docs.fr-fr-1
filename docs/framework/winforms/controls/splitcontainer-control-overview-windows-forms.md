---
title: "Vue d'ensemble du contrôle SplitContainer (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SplitContainer
helpviewer_keywords: SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10f18c46c85ed840b6625d9ed754d1d036a80975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Vue d'ensemble du contrôle SplitContainer (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.SplitContainer> peut être considéré comme un composite ; il s'agit de deux panneaux séparés par une barre mobile. Quand le pointeur de la souris est sur la barre, il change de forme pour montrer que la barre est mobile.  
  
> [!IMPORTANT]
>  Dans le **boîte à outils**, <xref:System.Windows.Forms.SplitContainer> contrôle remplace le <xref:System.Windows.Forms.Splitter> contrôle qui existait dans la version précédente de [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. Il vaut beaucoup mieux utiliser le contrôle <xref:System.Windows.Forms.SplitContainer> que le contrôle <xref:System.Windows.Forms.Splitter>. Le <xref:System.Windows.Forms.Splitter> classe est toujours inclus dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour la compatibilité avec les applications existantes, mais nous vous encourageons vivement à utiliser le <xref:System.Windows.Forms.SplitContainer> contrôle pour les nouveaux projets.  
  
 Avec la <xref:System.Windows.Forms.SplitContainer> contrôle, vous pouvez créer des interfaces utilisateur complexes ; souvent, une sélection dans un panneau détermine les objets affichés dans l’autre panneau. Cette disposition est très efficace pour afficher et parcourir des informations. Avoir deux panneaux vous permet de regrouper des informations dans les zones et de la barre, ou « séparateur », permet aux utilisateurs de redimensionner les panneaux.  
  
 Plusieurs <xref:System.Windows.Forms.SplitContainer> contrôle peut également être imbriquée, la seconde <xref:System.Windows.Forms.SplitContainer> contrôle orientée horizontalement, pour créer des panneaux inférieur et supérieur.  
  
 N’oubliez pas que le <xref:System.Windows.Forms.SplitContainer> contrôle est accessible par le clavier par défaut ; les utilisateurs peuvent appuyer sur les touches de direction pour déplacer le séparateur si la <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> est définie sur `false`.  
  
 Le <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriété de la <xref:System.Windows.Forms.SplitContainer> contrôle détermine la direction du séparateur et non du contrôle lui-même. Par conséquent, lorsque cette propriété a la valeur <xref:System.Windows.Forms.Orientation.Vertical>, le séparateur s’exécute de haut en bas, en créant des panneaux gauche et droite.  
  
 En outre, sachez que la valeur de la <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriété varie selon la valeur de la <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriété. Pour plus d’informations, consultez <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriété.  
  
 Vous pouvez également limiter la taille et le déplacement de la <xref:System.Windows.Forms.SplitContainer> contrôle. Le <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> propriété détermine le panneau qui reste la même taille après le <xref:System.Windows.Forms.SplitContainer> contrôle est redimensionné et le <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> propriété détermine si le séparateur est mobile par le clavier ou la souris.  
  
> [!NOTE]
>  Même si le <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> est définie sur `true`, le séparateur peut encore être déplacé par programmation ; par exemple, à l’aide de la <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> propriété.  
  
 Enfin, chaque panneau de configuration de la <xref:System.Windows.Forms.SplitContainer> contrôle possède des propriétés pour déterminer sa taille individuelle.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriétés, méthodes et événements couramment utilisés  
  
|Nom|Description|  
|----------|-----------------|  
|Propriété <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Détermine le panneau qui reste la même taille après le <xref:System.Windows.Forms.SplitContainer> contrôle est redimensionné.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Détermine si le séparateur peut être déplacé avec la souris ou du clavier.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A>|Détermine si le séparateur est disposé verticalement ou horizontalement.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Détermine la distance en pixels du bord gauche ou supérieur à la barre de fractionnement mobile.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Détermine la distance minimale, en pixels, que le séparateur peut être déplacé par l’utilisateur.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>|Détermine l’épaisseur, en pixels, du séparateur.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>événement|Se produit lorsque le séparateur est en mouvement.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>événement|Se produit lorsque le séparateur a été déplacé.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Exemple de contrôle SplitContainer](http://msdn.microsoft.com/en-us/9015fad0-7108-4d85-a83a-a72d038c4f65)
