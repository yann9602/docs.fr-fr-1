---
title: "Comment : créer une liaison dans du code"
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
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f98190b2d0f48e931129dcf95f63b2ff6b616ccc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="1732a-102">Comment : créer une liaison dans du code</span><span class="sxs-lookup"><span data-stu-id="1732a-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="1732a-103">Cet exemple montre comment créer et définir un <xref:System.Windows.Data.Binding> dans le code.</span><span class="sxs-lookup"><span data-stu-id="1732a-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1732a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1732a-104">Example</span></span>  
 <span data-ttu-id="1732a-105">Le <xref:System.Windows.FrameworkElement> classe et le <xref:System.Windows.FrameworkContentElement> exposent toutes deux un `SetBinding` (méthode).</span><span class="sxs-lookup"><span data-stu-id="1732a-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="1732a-106">Si vous liez un élément qui hérite de ces classes, vous pouvez appeler la <xref:System.Windows.FrameworkElement.SetBinding%2A> directement la méthode.</span><span class="sxs-lookup"><span data-stu-id="1732a-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="1732a-107">L’exemple suivant crée une classe nommée, `MyData`, qui contient une propriété nommée `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="1732a-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="1732a-108">L’exemple suivant montre comment créer un objet de liaison pour définir la source de la liaison.</span><span class="sxs-lookup"><span data-stu-id="1732a-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="1732a-109">L’exemple utilise <xref:System.Windows.FrameworkElement.SetBinding%2A> pour lier la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété du `myText`, qui est un <xref:System.Windows.Controls.TextBlock> contrôle, `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="1732a-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="1732a-110">Pour l’exemple de code complet, consultez [uniquement par le Code de liaison, exemple](http://msdn.microsoft.com/en-us/764aaf0b-2216-4941-9548-9c98da18d1a6).</span><span class="sxs-lookup"><span data-stu-id="1732a-110">For the complete code sample, see [Code-only Binding Sample](http://msdn.microsoft.com/en-us/764aaf0b-2216-4941-9548-9c98da18d1a6).</span></span>  
  
 <span data-ttu-id="1732a-111">Au lieu d’appeler <xref:System.Windows.FrameworkElement.SetBinding%2A>, vous pouvez utiliser la <xref:System.Windows.Data.BindingOperations.SetBinding%2A> méthode statique de la <xref:System.Windows.Data.BindingOperations> classe.</span><span class="sxs-lookup"><span data-stu-id="1732a-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="1732a-112">L’exemple suivant, les appels <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pour lier `myText` à `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="1732a-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="1732a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1732a-113">See Also</span></span>  
 [<span data-ttu-id="1732a-114">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="1732a-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1732a-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="1732a-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
