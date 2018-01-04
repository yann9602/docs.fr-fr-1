---
title: "Comment : créer une liaison simple"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 108b532e3aea27571c8a3b1290d931e2b0769be9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="8cc88-102">Comment : créer une liaison simple</span><span class="sxs-lookup"><span data-stu-id="8cc88-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="8cc88-103">Cet exemple vous montre comment créer un simple <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="8cc88-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cc88-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8cc88-104">Example</span></span>  
 <span data-ttu-id="8cc88-105">Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="8cc88-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="8cc88-106">Le `Person` objet est défini dans l’espace de noms appelé `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="8cc88-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="8cc88-107">L’exemple suivant instancie le `Person` de l’objet avec un `PersonName` valeur de propriété `Joe`.</span><span class="sxs-lookup"><span data-stu-id="8cc88-107">The following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="8cc88-108">Cette opération est effectuée le `Resources` section et affecté un `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="8cc88-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xaml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 <span data-ttu-id="8cc88-109">Pour lier à la `PersonName` propriété, vous devez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8cc88-109">To bind to the `PersonName` property you would do the following:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="8cc88-110">Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».</span><span class="sxs-lookup"><span data-stu-id="8cc88-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc88-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cc88-111">See Also</span></span>  
 [<span data-ttu-id="8cc88-112">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="8cc88-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="8cc88-113">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="8cc88-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
