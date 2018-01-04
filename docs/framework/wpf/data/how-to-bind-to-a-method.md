---
title: "Comment : effectuer une liaison à une méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45f2a141b09c52085c13803b8d338fdc9eebf135
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="098a3-102">Comment : effectuer une liaison à une méthode</span><span class="sxs-lookup"><span data-stu-id="098a3-102">How to: Bind to a Method</span></span>
<span data-ttu-id="098a3-103">L’exemple suivant montre comment lier une méthode à l’aide de <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="098a3-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="098a3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="098a3-104">Example</span></span>  
 <span data-ttu-id="098a3-105">Dans cet exemple, `TemperatureScale` est une classe qui possède une méthode `ConvertTemp`, qui prend deux paramètres (`TempType)`, un de type `double` et l’autre de type `enum`) et convertit la valeur donnée d’une échelle de température à une autre.</span><span class="sxs-lookup"><span data-stu-id="098a3-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="098a3-106">Dans l’exemple suivant, un <xref:System.Windows.Data.ObjectDataProvider> est utilisé pour instancier le `TemperatureScale` objet.</span><span class="sxs-lookup"><span data-stu-id="098a3-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="098a3-107">La méthode `ConvertTemp` est appelée avec deux paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="098a3-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="098a3-108">Maintenant que la méthode est disponible en tant que ressource, vous pouvez effectuer la liaison à ses résultats.</span><span class="sxs-lookup"><span data-stu-id="098a3-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="098a3-109">Dans l’exemple suivant, la <xref:System.Windows.Controls.TextBox.Text%2A> propriété de la <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> de la <xref:System.Windows.Controls.ComboBox> sont liées aux deux paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="098a3-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="098a3-110">Cela permet aux utilisateurs de spécifier la température à convertir et l’échelle de température à partir de laquelle effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="098a3-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="098a3-111">Notez que <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> a la valeur `true` étant donné que nous créons une liaison avec le <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> propriété de la <xref:System.Windows.Data.ObjectDataProvider> instance et pas les propriétés de l’objet encapsulé par le <xref:System.Windows.Data.ObjectDataProvider> (le `TemperatureScale` objet).</span><span class="sxs-lookup"><span data-stu-id="098a3-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="098a3-112">Le <xref:System.Windows.Controls.ContentControl.Content%2A> du dernier <xref:System.Windows.Controls.Label> met à jour lorsque l’utilisateur modifie le contenu de la <xref:System.Windows.Controls.TextBox> ou la sélection de la <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="098a3-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="098a3-113">Le convertisseur `DoubleToString` prend une valeur double et la convertit en une chaîne dans le <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (à partir de la source de liaison à la cible de liaison, qui est la <xref:System.Windows.Controls.TextBox.Text%2A> propriété) et convertit un `string` à un `double` dans le <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span><span class="sxs-lookup"><span data-stu-id="098a3-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="098a3-114">Le `InvalidationCharacterRule` est un <xref:System.Windows.Controls.ValidationRule> qui vérifie les caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="098a3-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="098a3-115">Le modèle d’erreur par défaut, qui est une bordure rouge autour de le <xref:System.Windows.Controls.TextBox>, apparaît pour signaler aux utilisateurs la valeur d’entrée n’est pas une valeur double.</span><span class="sxs-lookup"><span data-stu-id="098a3-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098a3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="098a3-116">See Also</span></span>  
 [<span data-ttu-id="098a3-117">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="098a3-117">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [<span data-ttu-id="098a3-118">Effectuer une liaison à une énumération</span><span class="sxs-lookup"><span data-stu-id="098a3-118">Bind to an Enumeration</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
