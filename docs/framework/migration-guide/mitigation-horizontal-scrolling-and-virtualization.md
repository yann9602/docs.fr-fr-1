---
title: "Atténuation : Défilement horizontal et virtualisation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bafd9b-a3b3-4f92-8241-2aad254fb1a9
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40eaf185e9c0c60493e9a2e5428c58b7463789fe
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-horizontal-scrolling-and-virtualization"></a>Atténuation : Défilement horizontal et virtualisation
Cette modification s’applique à un <xref:System.Windows.Controls.ItemsControl> qui effectue sa propre virtualisation dans le sens orthogonal vers la direction de défilement principale. (L’exemple principal est un contrôle <xref:System.Windows.Controls.DataGrid> dont l’attribut <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> a la valeur `true`.)  Le résultat de certaines opérations de défilement horizontales a été modifié afin de produire des résultats qui sont plus intuitifs et plus analogues par rapport aux résultats des opérations verticales comparables.  Les opérations spécifiques comprennent **Défilement ici** et **Bord droit** pour utiliser les noms à partir du menu obtenu en double-cliquant sur une barre de défilement horizontale.  Toutes deux calculent un décalage candidat et appellent <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.  Après défilement vers le nouveau décalage, les définitions de « ici » ou « bord droit » peuvent avoir changé, car le nouveau contenu dévirtualisé a modifié la valeur de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName>.  
  
## <a name="description-of-the-change"></a>Description de la modification  
 Avant [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], l’opération de défilement utilisait simplement le décalage final, même si ce n’est plus « ici » ou le « bord droit ».  Cela entraîne des effets tels que le « rebondissement » du curseur de défilement, comme illustré dans l’exemple.  Supposons qu’un contrôle <xref:System.Windows.Controls.DataGrid> a un attribut <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> avec la valeur 1000 et un attribut <xref:System.Windows.FrameworkElement.Width%2A> avec la valeur 200.  Un défilement vers le « Bord droit » utilise un décalage potentiel de 1000-200 = 800.  Pendant le défilement vers ce décalage, les nouvelles colonnes sont dévirtualisées. Supposons qu’elles sont très larges, de sorte que <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> passe à 2000.  Le défilement se termine avec <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>=800, et le curseur « rebondit » à proximité du centre de la barre de défilement (précisément à 800/2000 = 40 %).  
  
 À compter de [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], un nouveau décalage potentiel est recalculé lorsque cette situation se produit. (C’est déjà comme cela que le défilement vertical fonctionne.)  
  
## <a name="impact"></a>Impact  
 Le changement génère une expérience plus prévisible et intuitive pour l’utilisateur final, mais il peut aussi affecter toute application qui dépend de la valeur exacte de <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> après un défilement horizontal, qu’il s’agisse d’un appel explicite à <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName> ou d’un appel effectué par l’utilisateur final.  
  
## <a name="mitigation"></a>Atténuation  
 Une application qui utilise une valeur prédite pour <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> doit être changée afin de récupérer la valeur réelle (et la valeur de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>) après tout défilement horizontal susceptible de modifier <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> en raison de la dévirtualisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)

