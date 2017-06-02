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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>Atténuation : Culture et opérations de répartiteur dans les applications WPF
Dans les applications qui ciblent le .NET Framework 4.6 et le .NET Framework 4.6.1, les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> qui sont effectuées dans un <xref:System.Windows.Threading.Dispatcher> sont perdues à la fin de cette opération de répartiteur. De même, les modifications apportées à <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en dehors d’une opération de répartiteur peuvent ne pas être répercutées quand cette opération est exécutée.  
  
 Cela est dû à une modification de <xref:System.Threading.ExecutionContext> qui entraîne le stockage de <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> dans le contexte d’exécution. Les opérations de répartiteur WPF stockent le contexte d’exécution utilisé pour commencer l’opération et restaurer le contexte précédent lorsque l’opération est terminée. Étant donné que <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> font désormais partie de ce contexte, les modifications qui leur sont apportées dans une opération de répartiteur ne sont pas conservées en dehors de cette opération.  
  
## <a name="impact"></a>Impact  
 D’un point de vue pratique, cela signifie que les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> peuvent ne pas circuler entre les rappels d’interface utilisateur WPF et tout autre code dans une application WPF.  
  
## <a name="mitigation"></a>Atténuation  
 Les applications affectées par ce changement peuvent contourner ce problème de deux manières :  
  
-   En stockant le <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> souhaité dans un champ et en vérifiant dans tous les corps d’opération <xref:System.Windows.Threading.Dispatcher> (notamment les gestionnaires de rappel d’événement d’interface utilisateur) que le <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> correct est défini.  
  
-   Étant donné que la modification de <xref:System.Threading.ExecutionContext> n’affecte que les applications WPF qui ciblent le .NET Framework 4.6 ou le .NET Framework 4.6.1, cette modification peut être évitée en ciblant le .NET Framework 4.5.2 ou en ciblant une version du .NET Framework commençant par 4.6.2.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
