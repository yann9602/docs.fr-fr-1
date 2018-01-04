---
title: "Comment : contrôler quand le texte TextBox met à jour la source"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c503eb3300aba4a44c5a013c62942e7a171ae96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="5ba04-102">Comment : contrôler quand le texte TextBox met à jour la source</span><span class="sxs-lookup"><span data-stu-id="5ba04-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="5ba04-103">Cette rubrique explique comment utiliser le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété pour contrôler le minutage des mises à jour de la source de liaison.</span><span class="sxs-lookup"><span data-stu-id="5ba04-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="5ba04-104">La rubrique utilise le <xref:System.Windows.Controls.TextBox> contrôle comme exemple.</span><span class="sxs-lookup"><span data-stu-id="5ba04-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ba04-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="5ba04-105">Example</span></span>  
 <span data-ttu-id="5ba04-106">Le <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> propriété a une valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="5ba04-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="5ba04-107">Cela signifie que si une application possède un <xref:System.Windows.Controls.TextBox> avec une limite de données <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> propriété, le texte que vous tapez dans le <xref:System.Windows.Controls.TextBox> ne met pas à jour la source jusqu'à ce que le <xref:System.Windows.Controls.TextBox> perd le focus (par exemple, lorsque vous cliquez en dehors de la <xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="5ba04-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="5ba04-108">Si vous souhaitez que la source soit mise à jour en tant que vous tapez, définissez la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de la liaison à <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="5ba04-108">If you want the source to get updated as you are typing, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="5ba04-109">Dans l’exemple suivant, la `Text` propriétés des deux le <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.TextBlock> sont liés à la même propriété source.</span><span class="sxs-lookup"><span data-stu-id="5ba04-109">In the following example, the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="5ba04-110">Le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété de la <xref:System.Windows.Controls.TextBox> liaison est définie sur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="5ba04-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 <span data-ttu-id="5ba04-111">Par conséquent, le <xref:System.Windows.Controls.TextBlock> montre le même texte (car la source change) que l’utilisateur entre du texte dans le <xref:System.Windows.Controls.TextBox>, comme illustré par la capture d’écran suivante de l’exemple :</span><span class="sxs-lookup"><span data-stu-id="5ba04-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="5ba04-112">![Capture d’écran : exemple de liaison de données simple](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="5ba04-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="5ba04-113">Si vous disposez d’une boîte de dialogue ou un formulaire modifiables par l’utilisateur et que vous souhaitez différer les mises à jour de la source jusqu'à ce que l’utilisateur a fini de modifier les champs et clique sur « OK », vous pouvez définir le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur de vos liaisons à <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5ba04-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="5ba04-114">Lorsque vous définissez la <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, la valeur source change uniquement lorsque l’application appelle la <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ba04-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="5ba04-115">L’exemple suivant montre comment appeler <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pour `itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="5ba04-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="5ba04-116">Vous pouvez utiliser la même technique pour les propriétés d’autres contrôles, mais n’oubliez pas que la plupart des autres propriétés ont une valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valeur <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="5ba04-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="5ba04-117">Pour plus d’informations, consultez le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="5ba04-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ba04-118">Le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété porte sur la source des mises à jour et par conséquent concerne uniquement les <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons.</span><span class="sxs-lookup"><span data-stu-id="5ba04-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="5ba04-119">Pour <xref:System.Windows.Data.BindingMode.TwoWay> et <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons, l’objet source doit fournir des notifications de modification de propriété.</span><span class="sxs-lookup"><span data-stu-id="5ba04-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="5ba04-120">Vous pouvez consulter les exemples figurant dans cette rubrique pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="5ba04-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="5ba04-121">Vous pouvez également consulter la page [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="5ba04-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba04-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ba04-122">See Also</span></span>  
 [<span data-ttu-id="5ba04-123">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="5ba04-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
