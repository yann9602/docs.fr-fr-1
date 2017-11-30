---
title: "Comment : implémenter la validation de la liaison"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec860cc9cc58febd98d8642c98a50ec296592d02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="2ea65-102">Comment : implémenter la validation de la liaison</span><span class="sxs-lookup"><span data-stu-id="2ea65-102">How to: Implement Binding Validation</span></span>
<span data-ttu-id="2ea65-103">Cet exemple montre comment utiliser un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et un déclencheur de style pour fournir une rétroaction visuelle pour informer l’utilisateur lorsqu’une valeur non valide est entrée, basée sur une règle de validation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2ea65-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea65-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea65-104">Example</span></span>  
 <span data-ttu-id="2ea65-105">Le contenu textuel de la <xref:System.Windows.Controls.TextBox> dans l’exemple suivant est lié à la `Age` propriété (de type int) d’un objet de source de liaison nommée `ods`.</span><span class="sxs-lookup"><span data-stu-id="2ea65-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="2ea65-106">La liaison est configurée pour utiliser une règle de validation nommée `AgeRangeRule` afin que si l’utilisateur entre des caractères non numériques ou une valeur inférieure à 21 ou supérieure à 130, un point d’exclamation rouge apparaisse en regard de la zone de texte et une info-bulle contenant le message d’erreur s’affiche lorsque l’utilisateur déplace la souris sur la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="2ea65-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="2ea65-107">L’exemple suivant illustre l’implémentation de `AgeRangeRule`, qui hérite de <xref:System.Windows.Controls.ValidationRule> et remplace le <xref:System.Windows.Controls.ValidationRule.Validate%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="2ea65-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="2ea65-108">La méthode Int32.Parse() est appelée sur la valeur pour s’assurer qu’elle ne contient pas de caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="2ea65-108">The Int32.Parse() method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="2ea65-109">Le <xref:System.Windows.Controls.ValidationRule.Validate%2A> méthode retourne un <xref:System.Windows.Controls.ValidationResult> qui indique si la valeur est valide selon si une exception est interceptée lors de l’analyse et si la valeur de durée de vie est en dehors des limites inférieures et supérieur.</span><span class="sxs-lookup"><span data-stu-id="2ea65-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 <span data-ttu-id="2ea65-110">L’exemple suivant montre le personnalisé <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` qui crée un point d’exclamation rouge pour informer l’utilisateur d’une erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="2ea65-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="2ea65-111">Les modèles de contrôle sont utilisés pour redéfinir l’apparence d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ea65-111">Control templates are used to redefine the appearance of a control.</span></span>  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 <span data-ttu-id="2ea65-112">Comme indiqué dans l’exemple suivant, la <xref:System.Windows.Controls.ToolTip> qui affiche le message d’erreur est créé à l’aide du style nommé `textBoxInError`.</span><span class="sxs-lookup"><span data-stu-id="2ea65-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="2ea65-113">Si la valeur de <xref:System.Windows.Controls.Validation.HasError%2A> est `true`, le déclencheur définit l’info-bulle d’actuel <xref:System.Windows.Controls.TextBox> sa première erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="2ea65-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="2ea65-114">Le <xref:System.Windows.Data.Binding.RelativeSource%2A> a la valeur <xref:System.Windows.Data.RelativeSourceMode.Self>, qui fait référence à l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="2ea65-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 <span data-ttu-id="2ea65-115">Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](http://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="2ea65-115">For the complete example, see [Binding Validation Sample](http://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
 <span data-ttu-id="2ea65-116">Notez que si vous ne fournissez pas personnalisé <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> le modèle d’erreur par défaut s’affiche pour fournir une rétroaction visuelle à l’utilisateur lorsqu’il existe une erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="2ea65-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="2ea65-117">Pour plus d’informations, consultez la section relative à la validation de données de la rubrique [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2ea65-117">See "Data Validation" in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="2ea65-118">En outre, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une règle de validation intégrée qui capte les exceptions levées pendant la mise à jour de la propriété de source de liaison.</span><span class="sxs-lookup"><span data-stu-id="2ea65-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="2ea65-119">Pour plus d'informations, consultez <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="2ea65-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea65-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea65-120">See Also</span></span>  
 [<span data-ttu-id="2ea65-121">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="2ea65-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="2ea65-122">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2ea65-122">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
