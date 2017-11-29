---
title: "Comment : obtenir l'objet de liaison d'une propriété cible liée aux données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 498849cc0205775f88c21d90d12b45c6b71a5dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="189da-102">Comment : obtenir l'objet de liaison d'une propriété cible liée aux données</span><span class="sxs-lookup"><span data-stu-id="189da-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="189da-103">Cet exemple montre comment obtenir l’objet de liaison à partir d’une propriété cible liée à des données.</span><span class="sxs-lookup"><span data-stu-id="189da-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="189da-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="189da-104">Example</span></span>  
 <span data-ttu-id="189da-105">Vous pouvez procédez comme suit pour obtenir le <xref:System.Windows.Data.Binding> objet :</span><span class="sxs-lookup"><span data-stu-id="189da-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  <span data-ttu-id="189da-106">Vous devez spécifier la propriété de dépendance pour la liaison de votre choix car il est possible que plusieurs propriétés de l’objet cible utilisent la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="189da-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="189da-107">Vous pouvez également obtenir le <xref:System.Windows.Data.BindingExpression> , puis d’obtenir la valeur de la <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="189da-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="189da-108">Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](http://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="189da-108">For the complete example see [Binding Validation Sample](http://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="189da-109">Si votre liaison est un <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="189da-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="189da-110">S’il s’agit un <xref:System.Windows.Data.PriorityBinding>, utilisez <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="189da-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="189da-111">Si vous ne savez pas si la propriété cible est liée à l’aide un <xref:System.Windows.Data.Binding>, un <xref:System.Windows.Data.MultiBinding>, ou un <xref:System.Windows.Data.PriorityBinding>, vous pouvez utiliser <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="189da-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189da-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="189da-112">See Also</span></span>  
 [<span data-ttu-id="189da-113">Créer une liaison dans du code</span><span class="sxs-lookup"><span data-stu-id="189da-113">Create a Binding in Code</span></span>](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [<span data-ttu-id="189da-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="189da-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
