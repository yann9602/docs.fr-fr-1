---
title: "Utilisation des événements du clavier"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19bad48188a039baeeb6365a2cd38671f83fca4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-keyboard-events"></a>Utilisation des événements du clavier
La plupart des programmes Windows Forms traitent l'entrée au clavier en gérant les événements de clavier. Cette rubrique fournit une vue d'ensemble des événements de clavier, explique quand utiliser chaque événement et détaille les données fournies pour chaque événement.  Consultez également [vue d’ensemble des gestionnaires d’événements (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [vue d’ensemble des événements (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\)).  
  
## <a name="keyboard-events"></a>Événements de clavier  
 Windows Forms fournit deux événements qui se produisent quand l'utilisateur appuie sur une touche du clavier et un événement qui se produit quand l'utilisateur relâche une touche du clavier :  
  
-   L'événement <xref:System.Windows.Forms.Control.KeyDown> se produit une fois.  
  
-   L'événement <xref:System.Windows.Forms.Control.KeyPress>, qui peut se produire plusieurs fois quand l'utilisateur maintient la même touche enfoncée.  
  
-   L'événement <xref:System.Windows.Forms.Control.KeyUp> se produit une fois quand l'utilisateur relâche une touche.  
  
 Quand l'utilisateur appuie sur une touche, Windows Forms détermine quel événement déclencher selon que le message de clavier spécifie une touche de caractère ou une touche physique. Pour plus d’informations sur les caractères et les touches physiques, consultez [fonctionnement des entrées au clavier](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
 Le tableau suivant décrit les trois événements de clavier.  
  
|Événements de clavier|Description|Résultats|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|Cet événement est déclenché quand l'utilisateur appuie sur une touche physique.|Le gestionnaire de <xref:System.Windows.Forms.Control.KeyDown> reçoit :<br /><br /> <ul><li>un paramètre <xref:System.Windows.Forms.KeyEventArgs>, qui fournit la propriété <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (qui spécifie un bouton de clavier physique) ;</li><li>la propriété <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> (Maj, Ctrl ou Alt) ;</li><li>la propriété <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> (qui combine le code de touche et le modificateur). Le paramètre <xref:System.Windows.Forms.KeyEventArgs> fournit également :<br /><br /> <ul><li>la propriété <xref:System.Windows.Forms.KeyEventArgs.Handled%2A>, qui peut être définie pour empêcher le contrôle sous-jacent de recevoir la touche ;</li><li>la propriété <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A>, qui peut être utilisée pour supprimer les événements <xref:System.Windows.Forms.Control.KeyPress> et <xref:System.Windows.Forms.Control.KeyUp> pour cette séquence de touches.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|Cet événement est déclenché quand la ou les touches enfoncées génèrent un caractère. Par exemple, l'utilisateur appuie sur les touches Maj et « a », ce qui produit un caractère « A » majuscule.|<xref:System.Windows.Forms.Control.KeyPress> est déclenché après <xref:System.Windows.Forms.Control.KeyDown>.<br /><br /> <ul><li>Le gestionnaire de <xref:System.Windows.Forms.Control.KeyPress> reçoit :</li><li>un paramètre <xref:System.Windows.Forms.KeyPressEventArgs>, qui contient le code de caractère de la touche qui a été enfoncée. Ce code de caractère est unique à chaque combinaison touche de caractère/touche de modification.<br /><br />     Par exemple, la touche « A » génère :<br /><br /> <ul><li>le code de caractère 65, si elle est enfoncée avec la touche Maj ;</li><li>ou la touche Verr. Maj, 97, si elle est activée seule,</li><li>Et 1, si elle est enfoncée avec la touche Ctrl.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|Cet événement est déclenché quand l’utilisateur relâche une touche physique.|Le gestionnaire de <xref:System.Windows.Forms.Control.KeyUp> reçoit :<br /><br /> <ul><li>un paramètre <xref:System.Windows.Forms.KeyEventArgs> :<br /><br /> <ul><li>qui fournit la propriété <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (qui spécifie un bouton de clavier physique) ;</li><li>la propriété <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> (Maj, Ctrl ou Alt) ;</li><li>la propriété <xref:System.Globalization.SortKey.KeyData%2A> (qui combine le code de touche et le modificateur).</li></ul></li></ul>|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrée au clavier dans une application Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Fonctionnement de l’entrée au clavier](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
