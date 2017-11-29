---
title: "Comment : naviguer au sein des données dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c754bba18e93f63306701381f66af04b593c473
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="21703-102">Comment : naviguer au sein des données dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21703-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="21703-103">Dans une application Windows, pour parcourir les enregistrements dans une source de données le plus simple consiste à lier un <xref:System.Windows.Forms.BindingSource> à la source de données, puis lier les contrôles à le <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="21703-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="21703-104">Vous pouvez ensuite utiliser la méthode de navigation intégrée sur le <xref:System.Windows.Forms.BindingSource> telle une <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> et <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span><span class="sxs-lookup"><span data-stu-id="21703-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="21703-105">À l’aide de ces méthodes s’ajuste le <xref:System.Windows.Forms.BindingSource.Position%2A> et <xref:System.Windows.Forms.BindingSource.Current%2A> propriétés de la <xref:System.Windows.Forms.BindingSource> en conséquence.</span><span class="sxs-lookup"><span data-stu-id="21703-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="21703-106">Vous pouvez également rechercher un élément et définissez-le en tant que l’élément actuel en définissant le <xref:System.Windows.Forms.BindingSource.Position%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="21703-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="21703-107">Pour incrémenter la position dans une source de données</span><span class="sxs-lookup"><span data-stu-id="21703-107">To increment the position in a data source</span></span>  
  
1.  <span data-ttu-id="21703-108">Définir le <xref:System.Windows.Forms.BindingSource.Position%2A> propriété de la <xref:System.Windows.Forms.BindingSource> de vos données liées à la position de l’enregistrement à atteindre.</span><span class="sxs-lookup"><span data-stu-id="21703-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="21703-109">L’exemple suivant illustre l’utilisation de la <xref:System.Windows.Forms.BindingSource.MoveNext%2A> méthode de la <xref:System.Windows.Forms.BindingSource> pour incrémenter la <xref:System.Windows.Forms.BindingSource.Position%2A> propriété lorsque le `nextButton` un clic sur.</span><span class="sxs-lookup"><span data-stu-id="21703-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="21703-110">Le <xref:System.Windows.Forms.BindingSource> est associé le `Customers` table d’un dataset `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="21703-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21703-111">Définition de la <xref:System.Windows.Forms.BindingSource.Position%2A> propriété avec une valeur au-delà du premier ou dernier enregistrement n’entraîne pas d’erreur, comme le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pas vous permettra de définir la position à une valeur en dehors des limites de la liste.</span><span class="sxs-lookup"><span data-stu-id="21703-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="21703-112">S’il est important dans votre application pour savoir si vous avez dépassé le premier ou dernier enregistrement, inclure une logique permettant de tester si vous dépassez le nombre d’éléments de données.</span><span class="sxs-lookup"><span data-stu-id="21703-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="21703-113">Pour vérifier si vous avez dépassé la fin ou au début</span><span class="sxs-lookup"><span data-stu-id="21703-113">To check whether you have passed the end or beginning</span></span>  
  
1.  <span data-ttu-id="21703-114">Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.BindingSource.PositionChanged>.</span><span class="sxs-lookup"><span data-stu-id="21703-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="21703-115">Dans le gestionnaire, vous pouvez tester si la valeur de position proposée a dépassé le nombre d’éléments de données réelles.</span><span class="sxs-lookup"><span data-stu-id="21703-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="21703-116">L’exemple suivant illustre comment vous pouvez tester si vous avez atteint le dernier élément de données.</span><span class="sxs-lookup"><span data-stu-id="21703-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="21703-117">Dans l’exemple, si vous êtes sur le dernier élément, le **suivant** bouton sur le formulaire est désactivé.</span><span class="sxs-lookup"><span data-stu-id="21703-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21703-118">Gardez à l’esprit que, vous modifiez la liste vous naviguez dans le code, vous devez réactiver la **suivant** bouton, afin que les utilisateurs peuvent rechercher toute la longueur de la nouvelle liste.</span><span class="sxs-lookup"><span data-stu-id="21703-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="21703-119">En outre, sachez que ci-dessus <xref:System.Windows.Forms.BindingSource.PositionChanged> événement spécifique <xref:System.Windows.Forms.BindingSource> vous travaillez doit être associé à sa méthode de gestion d’événements.</span><span class="sxs-lookup"><span data-stu-id="21703-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="21703-120">Voici un exemple d’une méthode permettant de gérer le <xref:System.Windows.Forms.BindingSource.PositionChanged> événement :</span><span class="sxs-lookup"><span data-stu-id="21703-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="21703-121">Pour rechercher un élément et le définir comme élément actuel</span><span class="sxs-lookup"><span data-stu-id="21703-121">To find an item and set it as the current item</span></span>  
  
1.  <span data-ttu-id="21703-122">Rechercher l’enregistrement que vous souhaitez définir comme élément actuel.</span><span class="sxs-lookup"><span data-stu-id="21703-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="21703-123">Ce faire, vous pouvez utiliser la <xref:System.Windows.Forms.BindingSource.Find%2A> méthode de la <xref:System.Windows.Forms.BindingSource>, si votre source de données implémente <xref:System.ComponentModel.IBindingList>.</span><span class="sxs-lookup"><span data-stu-id="21703-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="21703-124">Quelques exemples de données sources qui implémentent <xref:System.ComponentModel.IBindingList> sont <xref:System.ComponentModel.BindingList%601> et <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="21703-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="21703-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21703-125">See Also</span></span>  
 [<span data-ttu-id="21703-126">Sources de données prises en charge par les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21703-126">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [<span data-ttu-id="21703-127">Notification de modifications dans la liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21703-127">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="21703-128">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21703-128">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="21703-129">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21703-129">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
