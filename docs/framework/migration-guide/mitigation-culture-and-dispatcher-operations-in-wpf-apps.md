---
title: "Atténuation : Culture et opérations de répartiteur dans les applications WPF | Microsoft Docs"
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
ms.assetid: 455c1452-8ce0-45ae-a092-21fb8edf1cac
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>Atténuation : Culture et opérations de répartiteur dans les applications WPF
Dans les applications qui ciblent le .NET Framework 4.6 et 4.6.1, les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> au sein d’un <xref:System.Windows.Threading.Dispatcher> seront perdues à la fin de l’opération de répartiteur. De même, les modifications apportées à <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en dehors d’une opération de répartiteur peuvent ne pas être reflétées au moment où s’exécute l’opération.  
  
 Cela est dû à une modification dans <xref:System.Threading.ExecutionContext> qui provoque le stockage de <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> dans le contexte d’exécution. Les opérations de répartiteur WPF stockent le contexte d’exécution utilisé pour commencer l’opération et restaurer le contexte précédent lorsque l’opération est terminée. Étant donné que <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> font désormais partie de ce contexte, les modifications qui leur sont apportées dans une opération de répartiteur ne persistent pas en dehors de l’opération.  
  
## <a name="impact"></a>Impact  
 Concrètement, cela signifie que les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> peuvent ne pas être transmises entre les rappels d’interface utilisateur de WPF et un autre code de l’application WPF.  
  
## <a name="mitigation"></a>Atténuation  
 Les applications affectées par ce changement peuvent contourner ce problème de deux manières :  
  
-   En stockant <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> dans un champ, puis en vérifiant dans tous les corps d’opérations <xref:System.Windows.Threading.Dispatcher> (y compris les gestionnaires de rappels d’événements de l’interface utilisateur) que les bons <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont définis.  
  
-   Étant donné que la modification de <xref:System.Threading.ExecutionContext> n’affecte que les applications WPF qui ciblent .NET Framework 4.6 ou .NET Framework 4.6.1, cette modification peut être évitée en ciblant .NET Framework 4.5.2 ou en ciblant une version du .NET Framework commençant par 4.6.2.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
