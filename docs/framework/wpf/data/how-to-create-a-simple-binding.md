---
title: "Comment : créer une liaison simple"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73ed25406aa398aa35c275b20da1deee48b119ab
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="f231a-102">Comment : créer une liaison simple</span><span class="sxs-lookup"><span data-stu-id="f231a-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="f231a-103">Cet exemple vous montre comment créer un simple <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="f231a-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f231a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f231a-104">Example</span></span>  
 <span data-ttu-id="f231a-105">Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="f231a-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="f231a-106">Le `Person` objet est défini dans l’espace de noms appelé `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="f231a-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="f231a-107">L’exemple suivant instancie le `Person` de l’objet avec un `PersonName` valeur de propriété `Joe`.</span><span class="sxs-lookup"><span data-stu-id="f231a-107">The following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="f231a-108">Cette opération est effectuée le `Resources` section et affecté un `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="f231a-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml)]  
  
 <span data-ttu-id="f231a-109">Pour lier à la `PersonName` propriété, vous devez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f231a-109">To bind to the `PersonName` property you would do the following:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="f231a-110">Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».</span><span class="sxs-lookup"><span data-stu-id="f231a-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f231a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f231a-111">See Also</span></span>  
 [<span data-ttu-id="f231a-112">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="f231a-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f231a-113">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="f231a-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
