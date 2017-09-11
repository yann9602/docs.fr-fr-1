---
title: "Atténuation : Culture et opérations de répartiteur dans les applications WPF"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41fc52679884d547809f1c1e9f47e29eb668cb8e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a><span data-ttu-id="0391e-102">Atténuation : Culture et opérations de répartiteur dans les applications WPF</span><span class="sxs-lookup"><span data-stu-id="0391e-102">Mitigation: Culture and Dispatcher Operations in WPF Apps</span></span>
<span data-ttu-id="0391e-103">Dans les applications qui ciblent le .NET Framework 4.6 et le .NET Framework 4.6.1, les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> qui sont effectuées dans un <xref:System.Windows.Threading.Dispatcher> sont perdues à la fin de cette opération de répartiteur.</span><span class="sxs-lookup"><span data-stu-id="0391e-103">In apps that target the .NET Framework 4.6 and the .NET Framework 4.6.1, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties that are made within a <xref:System.Windows.Threading.Dispatcher> are lost at the end of that dispatcher operation.</span></span> <span data-ttu-id="0391e-104">De même, les modifications apportées à <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> en dehors d’une opération de répartiteur peuvent ne pas être répercutées quand cette opération est exécutée.</span><span class="sxs-lookup"><span data-stu-id="0391e-104">Similarly, changes to <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> made outside of a dispatcher operation may not be reflected when that operation executes.</span></span>  
  
 <span data-ttu-id="0391e-105">Cela est dû à une modification de <xref:System.Threading.ExecutionContext> qui entraîne le stockage de <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> dans le contexte d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0391e-105">This is due to a change in <xref:System.Threading.ExecutionContext> that causes the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to be stored in the execution context.</span></span> <span data-ttu-id="0391e-106">Les opérations de répartiteur WPF stockent le contexte d’exécution utilisé pour commencer l’opération et restaurer le contexte précédent lorsque l’opération est terminée.</span><span class="sxs-lookup"><span data-stu-id="0391e-106">WPF dispatcher operations store the execution context used to begin the operation and restore the previous context when the operation is completed.</span></span> <span data-ttu-id="0391e-107">Étant donné que <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> font désormais partie de ce contexte, les modifications qui leur sont apportées dans une opération de répartiteur ne sont pas conservées en dehors de cette opération.</span><span class="sxs-lookup"><span data-stu-id="0391e-107">Because <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are now part of that context, changes to them within a dispatcher operation are not persisted outside of the operation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0391e-108">Impact</span><span class="sxs-lookup"><span data-stu-id="0391e-108">Impact</span></span>  
 <span data-ttu-id="0391e-109">D’un point de vue pratique, cela signifie que les modifications apportées aux propriétés <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> peuvent ne pas circuler entre les rappels d’interface utilisateur WPF et tout autre code dans une application WPF.</span><span class="sxs-lookup"><span data-stu-id="0391e-109">Practically, this means that changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties may not flow between WPF UI callbacks and other code in a WPF application.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0391e-110">Atténuation</span><span class="sxs-lookup"><span data-stu-id="0391e-110">Mitigation</span></span>  
 <span data-ttu-id="0391e-111">Les applications affectées par ce changement peuvent contourner ce problème de deux manières :</span><span class="sxs-lookup"><span data-stu-id="0391e-111">Apps affected by this change may work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="0391e-112">En stockant le <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> souhaité dans un champ et en vérifiant dans tous les corps d’opération <xref:System.Windows.Threading.Dispatcher> (notamment les gestionnaires de rappel d’événement d’interface utilisateur) que le <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> correct est défini.</span><span class="sxs-lookup"><span data-stu-id="0391e-112">By storing the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> in a field and checking in all <xref:System.Windows.Threading.Dispatcher> operation bodies (including UI event callback handlers) that the correct <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> is set.</span></span>  
  
-   <span data-ttu-id="0391e-113">Étant donné que la modification de <xref:System.Threading.ExecutionContext> n’affecte que les applications WPF qui ciblent le .NET Framework 4.6 ou le .NET Framework 4.6.1, cette modification peut être évitée en ciblant le .NET Framework 4.5.2 ou en ciblant une version du .NET Framework commençant par 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0391e-113">Because the change to <xref:System.Threading.ExecutionContext> only affects WPF apps that target the .NET Framework 4.6 or the .NET Framework 4.6.1, this change can be avoided by targeting the .NET Framework 4.5.2 or by targeting a version of the .NET Framework starting with 4.6.2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0391e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0391e-114">See Also</span></span>  
 [<span data-ttu-id="0391e-115">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="0391e-115">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

