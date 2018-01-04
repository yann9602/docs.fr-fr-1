---
title: "Comment : spécifier le sens de la liaison"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9944ff214a9dfe12b21e005c4e1998c249bf72b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="11db4-102">Comment : spécifier le sens de la liaison</span><span class="sxs-lookup"><span data-stu-id="11db4-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="11db4-103">Cet exemple montre comment spécifier si la liaison met à jour uniquement la propriété de la cible de liaison (cible), uniquement la propriété de la source de liaison (source), ou bien à la fois la propriété cible et la propriété source.</span><span class="sxs-lookup"><span data-stu-id="11db4-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11db4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="11db4-104">Example</span></span>  
 <span data-ttu-id="11db4-105">Vous utilisez le <xref:System.Windows.Data.Binding.Mode%2A> propriété pour spécifier la direction de la liaison.</span><span class="sxs-lookup"><span data-stu-id="11db4-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="11db4-106">La liste d’énumération suivante affiche les options disponibles pour les mises à jour de la liaison :</span><span class="sxs-lookup"><span data-stu-id="11db4-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="11db4-107"><xref:System.Windows.Data.BindingMode.TwoWay>met à jour la propriété cible ou la propriété chaque fois que la propriété cible ou la propriété source change.</span><span class="sxs-lookup"><span data-stu-id="11db4-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="11db4-108"><xref:System.Windows.Data.BindingMode.OneWay>met à jour la propriété cible uniquement lorsque la propriété source change.</span><span class="sxs-lookup"><span data-stu-id="11db4-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="11db4-109"><xref:System.Windows.Data.BindingMode.OneTime>met à jour la propriété cible uniquement lorsque l’application démarre ou lorsque le <xref:System.Windows.FrameworkElement.DataContext%2A> subit une modification.</span><span class="sxs-lookup"><span data-stu-id="11db4-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="11db4-110"><xref:System.Windows.Data.BindingMode.OneWayToSource>met à jour la propriété source lorsque la propriété cible change.</span><span class="sxs-lookup"><span data-stu-id="11db4-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="11db4-111"><xref:System.Windows.Data.BindingMode.Default>provoque la valeur par défaut <xref:System.Windows.Data.Binding.Mode%2A> valeur de propriété cible à utiliser.</span><span class="sxs-lookup"><span data-stu-id="11db4-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="11db4-112">Pour plus d’informations, consultez l’énumération <xref:System.Windows.Data.BindingMode>.</span><span class="sxs-lookup"><span data-stu-id="11db4-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="11db4-113">L'exemple suivant indique comment définir la propriété <xref:System.Windows.Data.Binding.Mode%2A>.</span><span class="sxs-lookup"><span data-stu-id="11db4-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="11db4-114">Pour détecter des modifications de source (applicables aux <xref:System.Windows.Data.BindingMode.OneWay> et <xref:System.Windows.Data.BindingMode.TwoWay> liaisons), la source doit implémenter un mécanisme de notification de modification de propriété approprié tel que <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="11db4-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="11db4-115">Consultez [Notification de modification de propriété implémentez](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) pour obtenir un exemple d’un <xref:System.ComponentModel.INotifyPropertyChanged> mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="11db4-115">See [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="11db4-116">Pour <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons, vous pouvez contrôler le minutage des mises à jour des source en définissant le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="11db4-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="11db4-117">Pour plus d'informations, voir <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="11db4-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11db4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11db4-118">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="11db4-119">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="11db4-119">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="11db4-120">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="11db4-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
