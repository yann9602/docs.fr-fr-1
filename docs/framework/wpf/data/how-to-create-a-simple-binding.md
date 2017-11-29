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
ms.openlocfilehash: a61844f917539f5d5e7c99299c8a33f4aa18450f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="01d45-102">Comment : créer une liaison simple</span><span class="sxs-lookup"><span data-stu-id="01d45-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="01d45-103">Cet exemple vous montre comment créer un simple <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="01d45-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d45-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="01d45-104">Example</span></span>  
 <span data-ttu-id="01d45-105">Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="01d45-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="01d45-106">Le `Person` objet est défini dans l’espace de noms appelé `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="01d45-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="01d45-107">L’exemple suivant instancie le `Person` de l’objet avec un `PersonName` valeur de propriété `Joe`.</span><span class="sxs-lookup"><span data-stu-id="01d45-107">The following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="01d45-108">Cette opération est effectuée le `Resources` section et affecté un `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="01d45-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xaml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 <span data-ttu-id="01d45-109">Pour lier à la `PersonName` propriété, vous devez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="01d45-109">To bind to the `PersonName` property you would do the following:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="01d45-110">Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».</span><span class="sxs-lookup"><span data-stu-id="01d45-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d45-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01d45-111">See Also</span></span>  
 [<span data-ttu-id="01d45-112">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="01d45-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="01d45-113">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="01d45-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
